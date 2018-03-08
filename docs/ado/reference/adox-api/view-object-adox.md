---
title: Visualizzare l'oggetto (ADOX) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af414c302459f093441f5f0f3fd0e60c1a95d973
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="view-object-adox"></a>Oggetto visualizzazione (ADOX)
Rappresenta un set filtrato di record o una tabella virtuale. Quando utilizzato in combinazione con l'oggetto ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto, il **vista** oggetto può essere utilizzato per l'aggiunta, eliminazione o modifica di viste.  
  
## <a name="remarks"></a>Osservazioni  
 Una vista è una tabella virtuale creata da altre tabelle del database o viste. Il **vista** oggetto consente di creare una visualizzazione senza dover conoscere o utilizzare la sintassi del provider "CREATE VIEW".  
  
 Con le proprietà di un **vista** dell'oggetto, è possibile:  
  
-   Identificare la vista con il [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Specificare l'oggetto ADO **comando** oggetto che può essere usato per aggiungere, eliminare o modificare le viste con la [comando](../../../ado/reference/adox-api/command-property-adox.md) proprietà.  
  
-   Restituire informazioni relative alla data con la [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) e [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) proprietà.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto View](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di raccolte di campi (VB) e viste](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Viste di esempio del metodo Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Raccolta di visualizzazioni, esempio di proprietà CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Viste di esempio del metodo Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Raccolta di oggetti View (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
