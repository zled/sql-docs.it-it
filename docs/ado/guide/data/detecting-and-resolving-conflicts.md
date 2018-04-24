---
title: Rilevamento e risoluzione dei conflitti | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- conflicts [ADO], detecting and resolving
- ADO, detecting and resolving conflicts
ms.assetid: b28fdd26-c1a4-40ce-a700-2b0c9d201514
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bb8451f5d4355b521f794501b4a431b02fc2f06
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="detecting-and-resolving-conflicts"></a>Rilevamento e risoluzione di conflitti
Se si utilizzano il Recordset in modalità immediata, è meno probabile per problemi di concorrenza si verifichi. D'altra parte, se l'applicazione utilizza la modalità batch di aggiornamento, potrebbe esserci una buona possibilità che un utente modifichi un record prima che vengano salvate le modifiche apportate da un altro utente modifica lo stesso record. In tal caso, è possibile utilizzare l'applicazione di gestire correttamente il conflitto. Potrebbe essere desideri che l'ultima persona di inviare un aggiornamento al server "wins". Oppure è possibile consentire all'utente più recente per decidere quali update deve avere la precedenza fornendo a quest'ultimo una scelta tra i due valori in conflitto.  
  
 In ogni caso, ADO fornisce le proprietà UnderlyingValue e OriginalValue dell'oggetto campo per gestire questi tipi di conflitti. Utilizzare queste proprietà in combinazione con il metodo Resync e la proprietà Filter del Recordset.  
  
## <a name="remarks"></a>Osservazioni  
 Se ADO rileva un conflitto durante un aggiornamento batch, un messaggio di avviso verrà aggiunto alla raccolta di errori. Pertanto, deve sempre cercare errori immediatamente dopo aver chiamato il metodo BatchUpdate e se vengono individuati, iniziare il test si presuppone che si è verificato un conflitto. Il primo passaggio è impostare la proprietà Filter per Recordset uguale a adFilterConflictingRecords. Consente di limitare la visualizzazione in Recordset ai record in conflitto. Se la proprietà RecordCount è uguale a zero dopo questo passaggio, si conosce che l'errore è stato generato da un valore diverso da un conflitto.  
  
 Quando si chiama il metodo BatchUpdate, ADO e il provider generano istruzioni SQL per eseguire aggiornamenti sull'origine dati. Tenere presente che determinate origini dati presentano limitazioni in cui è possono utilizzare i tipi di colonne in una clausola WHERE.  
  
 Successivamente, chiamare il metodo di risincronizzazione nel Recordset con l'argomento AffectRecords impostato su adAffectGroup e l'argomento ResyncValues impostato su adResyncUnderlyingValues. Il metodo Resync aggiorna i dati nell'oggetto Recordset corrente dal database sottostante. Utilizzando adAffectGroup, si garantisce che solo i record visibili con il filtro corrente l'impostazione, vale a dire, solo i record in conflitto, vengono sincronizzati con il database. Se si sta utilizzando un Recordset di grandi dimensioni, questo potrebbe rendere una differenza significativa. Impostazione dell'argomento ResyncValues su adResyncUnderlyingValues durante la chiamata di risincronizzazione, consente di garantire che la proprietà conterrà il valore (conflitto) dal database, che la proprietà Value manterrà il valore immesso dall'utente, e che la proprietà OriginalValue conterrà il valore originale per il campo (il valore della prima che venga effettuata l'ultima chiamata UpdateBatch ha esito positivo). È quindi possibile utilizzare questi valori per risolvere il conflitto a livello di codice o richiedere all'utente di selezionare un valore che verrà utilizzato.  
  
 Questa tecnica è illustrata nell'esempio di codice seguente. Nell'esempio viene creato in modo artificiale un conflitto utilizzando un oggetto Recordset distinto per modificare un valore nella tabella sottostante prima di chiamare UpdateBatch.  
  
```  
'BeginConflicts  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT * FROM Shippers WHERE ShipperID = 2"  
  
    'Open Rs and change a value  
    Set objRs1 = New ADODB.Recordset  
    Set objRs2 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Introduce a conflict at the db...  
    objRs2.Open strSQL, strConn, adOpenKeyset, adLockOptimistic, adCmdText  
    objRs2("Phone") = "(999) 555-9999"  
    objRs2.Update  
    objRs2.Close  
    Set objRs2 = Nothing  
  
    On Error Resume Next  
    objRs1.UpdateBatch  
  
    If objRs1.ActiveConnection.Errors.Count <> 0 Then  
        Dim intConflicts As Integer  
  
        intConflicts = 0  
  
        objRs1.Filter = adFilterConflictingRecords  
  
        intConflicts = objRs1.RecordCount  
  
        'Resync so we can see the UnderlyingValue and offer user a choice.  
        'This sample only displays all three values and resets to original.  
        objRs1.Resync adAffectGroup, adResyncUnderlyingValues  
  
        If intConflicts > 0 Then  
            strMsg = "A conflict occurred with updates for " & intConflicts & _  
                     " record(s)." & vbCrLf & "The values will be restored" & _  
                     " to their original values." & vbCrLf & vbCrLf  
  
            objRs1.MoveFirst  
            While Not objRs1.EOF  
              strMsg = strMsg & "SHIPPER = " & objRs1("CompanyName") & vbCrLf  
              strMsg = strMsg & "Value = " & objRs1("Phone").Value & vbCrLf  
              strMsg = strMsg & "UnderlyingValue = " & _  
                                 objRs1("Phone").UnderlyingValue & vbCrLf  
              strMsg = strMsg & "OriginalValue = " & _  
                                 objRs1("Phone").OriginalValue & vbCrLf  
              strMsg = strMsg & vbCrLf & "Original value has been restored."  
  
              MsgBox strMsg, vbOKOnly, _  
                    "Conflict " & objRs1.AbsolutePosition & _  
                    " of " & intConflicts  
  
              objRs1("Phone").Value = objRs1("Phone").OriginalValue  
              objRs1.MoveNext  
            Wend  
  
            objRs1.UpdateBatch adAffectGroup  
        Else  
            'Other error occurred. Minimal handling in this example.  
             strMsg = "Errors occurred during the update. " & _  
                        objRs1.ActiveConnection.Errors(0).Number & " " & _  
                        objRs1.ActiveConnection.Errors(0).Description  
        End If  
  
        On Error GoTo 0  
    End If  
  
    objRs1.MoveFirst  
    objRs1.Close  
    Set objRs1 = Nothing  
'EndConflicts  
```  
  
 È possibile utilizzare la proprietà Status del Record corrente o di un campo specifico per determinare il tipo di un conflitto si è verificato.  
  
 Per informazioni dettagliate sulla gestione degli errori, vedere [Error Handling](../../../ado/guide/data/error-handling.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](../../../ado/guide/data/batch-mode.md)
