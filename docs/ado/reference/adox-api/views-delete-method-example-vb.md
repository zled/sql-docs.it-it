---
title: Viste di esempio del metodo Delete (VB) | Documenti Microsoft
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
- Delete method [ADOX]
ms.assetid: 17df2a83-4166-4df8-8c17-0a33aaac8582
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d8990c77ac61b8c85ffe4d6d48cfcc80cdab77f6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="views-delete-method-example-vb"></a>Viste di esempio del metodo Delete (VB)
Il codice seguente viene illustrato come utilizzare il [eliminare](../../../ado/reference/adox-api/delete-method-adox-collections.md) metodo per eliminare una vista dal catalogo.  
  
```  
' BeginDeleteViewVB  
Sub Main()  
    On Error GoTo DeleteViewError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    'Delete the View  
    cat.Views.Delete "AllCustomers"  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteViewError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteViewVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Delete (metodo) (ADOX raccolte)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [Raccolta di visualizzazioni (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)

