---
title: Salvare e aprire l'esempio di metodi (VB) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26fa69e0c02dfffb208725f61c826068337a8b98
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="save-and-open-methods-example-vb"></a>Salvare e aprire l'esempio di metodi (VB)
Questi tre esempi viene illustrato come la [salvare](../../../ado/reference/ado-api/save-method.md) e [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodi possono essere utilizzati insieme.  
  
 Si supponga di dover effettuare un viaggio e che si voglia lungo una tabella da un database. Prima di procedere, si accede ai dati come un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) e salvarlo in un modulo da spostare. Quando si arriva a destinazione, si accede di **Recordset** come locale, disconnesso **Recordset**. Si apportano modifiche per il **Recordset**e quindi salvarlo nuovamente. Infine, quando si ritorna home, riconnettersi al database e aggiornarlo con le modifiche apportate in viaggio.  
  
 In primo luogo, accedere e salvare il ***autori*** tabella.  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 Si è arrivati a questo punto, la destinazione. L'accesso è necessario il ***autori*** tabella come un'unità locale disconnesso **Recordset**. È necessario disporre di **MSPersist** provider nel computer in cui si utilizza per accedere al file salvato, a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Infine, restituire home. Ora è possibile aggiornare il database con le modifiche.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Ulteriori informazioni su persistenza Recordset](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Metodo Save](../../../ado/reference/ado-api/save-method.md)
