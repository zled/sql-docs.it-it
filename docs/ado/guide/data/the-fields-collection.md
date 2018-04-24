---
title: Raccolta di campi | Documenti Microsoft
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
- Field object [ADO], fields collection
- Fields collection [ADO]
ms.assetid: 574cf36e-e5f5-403b-983c-749ef93c108f
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d26e2fb793dc1b4b6b757e17064760857b748ed8
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="the-fields-collection"></a>Raccolta di campi
Il **campi** insieme è uno degli insiemi intrinseci di ADO. Una raccolta è un set ordinato di elementi che può essere indicato come un'unità. Per ulteriori informazioni sulle raccolte di ADO, vedere [il modello a oggetti ADO](../../../ado/guide/data/ado-objects-and-collections.md).  
  
 Il **campi** raccolta contiene un **campo** oggetto per ogni campo (colonna) di **Recordset**. Come tutte le raccolte di ADO, ha **conteggio** e **elemento** proprietà, così come **Append** e **aggiornamento** metodi. Include inoltre **CancelUpdate**, **eliminare**, **Resync**, e **aggiornamento** metodi, che non sono disponibili in altre raccolte di ADO.  
  
## <a name="examining-the-fields-collection"></a>Esaminare la raccolta di campi  
 Si consideri il **campi** raccolta del campione **Recordset** introdotte in questa sezione. L'esempio **Recordset** è stata derivata dall'istruzione SQL  
  
```  
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE CategoryID = 7  
```  
  
 Pertanto, è necessario trovare che il **Recordset Fields** insieme contiene tre campi.  
  
```  
'BeginWalkFields  
    Dim objFields As ADODB.Fields  
    Dim intLoop As Integer  
  
    objRs.Open strSQL, strConnStr, adOpenForwardOnly, adLockReadOnly, adCmdText  
  
    Set objFields = objRs.Fields  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
    Next  
'EndWalkFields  
```  
  
 Questo codice determina semplicemente il numero di **campo** gli oggetti di **campi** insieme utilizzando la **conteggio** proprietà e scorre la raccolta, restituendo il valore di il **nome** proprietà per ogni **campo** oggetto. È possibile utilizzare molti altri **campo** proprietà per ottenere informazioni su un campo. Per ulteriori informazioni sull'esecuzione di query un **campo**, vedere [il campo oggetto](../../../ado/guide/data/the-field-object.md).  
  
## <a name="counting-columns"></a>Conteggio delle colonne  
 Come prevedibile, la **conteggio** proprietà restituisce il numero effettivo di **campo** gli oggetti il **campi** insieme. Poiché la numerazione dei membri di una raccolta inizia da zero, è consigliabile codificare sempre i cicli a partire dal membro zero e terminando con il valore di **conteggio** proprietà meno 1. Se si utilizza Microsoft Visual Basic e si desidera per scorrere in ciclo i membri di una raccolta senza il controllo il **conteggio** proprietà, utilizzare il **For Each... Avanti** comando.  
  
 Se il **conteggio** proprietà è zero, non sono presenti oggetti nella raccolta.  
  
## <a name="getting-to-the-field"></a>Guida per il campo  
 Come con qualsiasi insieme di ADO, il **elemento** proprietà la proprietà predefinita della raccolta. Restituisce i singoli **campo** oggetto specificato dal nome o l'indice passato. Pertanto, le istruzioni seguenti sono equivalenti per l'esempio **Recordset**:  
  
```  
objField = objRecordset.Fields.Item("ProductID")  
objField = objRecordset.Fields("ProductID")  
objField = objRecordset.Fields.Item(0)  
objField = objRecordset.Fields(0)  
```  
  
 Se questi metodi sono equivalenti, che è più adatta? Dipende. Utilizzo di un indice per recuperare un **campo** dalla raccolta è più veloce perché accede il **campo** direttamente senza dover eseguire una ricerca di stringa. D'altra parte, l'ordine dei **campi** all'interno della raccolta deve essere nota, e se l'ordine viene modificato, il riferimento di **del campo** indice dovrà essere modificato ogni volta che si verifica. Anche se leggermente più lento, utilizzando il nome del **campo** è più flessibile perché non variano in base all'ordine dei **campi** nella raccolta.  
  
## <a name="using-the-refresh-method"></a>Utilizzando il metodo di aggiornamento  
 A differenza di alcuni altri insiemi di ADO, utilizzando il **aggiornamento** metodo il **campi** raccolta non ha alcun effetto visibile. Per recuperare le modifiche dalla struttura di database sottostante, è necessario utilizzare il **Requery** metodo, o se il **Recordset** oggetto non supporta i segnalibri, il **MoveFirst**(metodo), che provoca il comando per essere eseguita nuovamente nel provider.  
  
## <a name="adding-fields-to-a-recordset"></a>Aggiunta di campi a un Recordset  
 Il **Append** metodo viene utilizzato per aggiungere i campi in un **Recordset**.  
  
 È possibile utilizzare il **Append** metodo per creare un **Recordset** a livello di codice senza dover aprire una connessione a un'origine dati. Se si verificherà un errore di run-time di **Append** metodo viene chiamato sul **campi** insieme di open **Recordset** o scegliere un **Recordset** in cui il **ActiveConnection** proprietà è stata impostata. È possibile aggiungere campi solo a un **Recordset** che non sia aperto e non è ancora stato connesso a un'origine dati. Tuttavia, per specificare valori per l'oggetto appena aggiunto **campi**, **Recordset** deve prima essere aperto.  
  
 Gli sviluppatori devono spesso una posizione per archiviare alcuni dati, o temporaneamente alcuni dati di agire come se proviene da un server in modo da partecipare nell'associazione di dati in un'interfaccia utente. ADO (in combinazione con il [servizio cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)) consente agli sviluppatori di compilare un oggetto vuoto **Recordset** oggetto che specifica le informazioni di colonna e chiamando **aprire**. Nell'esempio seguente, tre nuovi campi vengono aggiunti a un nuovo **Recordset** oggetto. Il **Recordset** è aperto, due nuovi record vengono aggiunti e **Recordset** è persistente in un file. (Per ulteriori informazioni su **Recordset** persistenza, vedere [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).)  
  
```  
'BeginFabricate  
    Dim objRs As ADODB.Recordset  
    Set objRs = New ADODB.Recordset  
  
    With objRs.Fields  
        .Append "StudentID", adChar, 11, adFldUpdatable  
        .Append "FullName", adVarChar, 50, adFldUpdatable  
        .Append "PhoneNmbr", adVarChar, 20, adFldUpdatable  
    End With  
  
    With objRs  
        .Open  
  
        .AddNew  
        .Fields(0) = "123-45-6789"  
        .Fields(1) = "John Doe"  
        .Fields(2) = "(425) 555-5555"  
        .Update  
  
        .AddNew  
        .Fields(0) = "123-45-6780"  
        .Fields(1) = "Jane Doe"  
        .Fields(2) = "(615) 555-1212"  
        .Update  
    End With  
  
    objRs.Save App.Path & "FabriTest.adtg", adPersistADTG  
  
    objRs.Close  
'EndFabricate  
```  
  
 L'utilizzo del **aggiungere campi** metodo differisce tra il **Recordset** oggetto e **Record** oggetto. Per ulteriori informazioni sul **Record** , vedere [record e i flussi](../../../ado/guide/data/records-and-streams.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di recordset gerarchici](../../../ado/guide/data/fabricating-hierarchical-recordsets.md)
