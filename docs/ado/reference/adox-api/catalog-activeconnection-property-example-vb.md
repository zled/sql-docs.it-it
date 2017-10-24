---
title: "Catalogo di esempio di proprietà ActiveConnection (VB) | Documenti Microsoft"
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
- ActiveConnection property [ADOX], Visual Basic example
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 382c25c68f911a48095593879a2657ac5409fc89
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-activeconnection-property-example-vb"></a>Esempio di proprietà ActiveConnection catalogo (VB)
L'impostazione di [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) proprietà a una connessione valida e aperta "aperta" nel catalogo. Da un catalogo aperto, è possibile accedere gli oggetti dello schema in esso contenuti.  
  
```  
' BeginOpenConnectionVB  
Sub Main()  
    On Error GoTo OpenConnectionError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Debug.Print cat.Tables(0).Type  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
OpenConnectionError:  
  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndOpenConnectionVB  
```  
  
 L'impostazione di **ActiveConnection** proprietà in una stringa di connessione valida anche "aperta" nel catalogo.  
  
```  
Attribute VB_Name = "Catalog"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Raccolta di tabelle (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Proprietà Type (tabella) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)

