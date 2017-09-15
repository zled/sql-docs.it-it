---
title: "Esempio di proprietà Status (campo) (VB) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 91c3418fea062661ffba94feb791d700301ff097
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="status-property-example-field-vb"></a>Esempio di proprietà Status (campo) (VB)
Nell'esempio seguente viene aperto un documento da una cartella di lettura/scrittura con la [Internet Publishing Provider](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Il [stato](../../../ado/reference/ado-api/status-property-ado-field.md) proprietà di un [campo](../../../ado/reference/ado-api/field-object.md) oggetto del [Record](../../../ado/reference/ado-api/record-object-ado.md) verrà impostata innanzitutto **adFieldPendingInsert**, quindi verrà aggiornata al **adFieldOk**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=http://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 L'esempio seguente elimina un noto **campo** da un **Record** aperto da un documento. Il **stato** verrà innanzitutto essere impostata su **adFieldOK**, quindi **su adFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Il codice seguente elimina un **campo** da un **Record** aperto in un documento di sola lettura. **Stato** verrà impostato su **adFieldPendingDelete**. In [aggiornamento](../../../ado/reference/ado-api/update-method.md), l'eliminazione non riuscirà e **stato** sarà **adFieldPendingDelete** più **adFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) Cancella l'in sospeso **stato** impostazione.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)   
 [Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Proprietà Status (campo ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
