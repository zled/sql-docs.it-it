---
title: ObjectTypeEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8eb88d7f3df60d8c54782d20af73e3fd5e917db3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Specifica il tipo di oggetto di database per cui impostare le autorizzazioni o la proprietà.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|L'oggetto è una colonna.|  
|**adPermObjDatabase**|3|L'oggetto è un database.|  
|**adPermObjProcedure**|4|L'oggetto è una procedura.|  
|**impostato su adPermObjProviderSpecific**|-1|L'oggetto è un tipo definito dal provider. Si verifica un errore se il *ObjectType* parametro **impostato su adPermObjProviderSpecific** e *ID tipo oggetto* non viene fornito.|  
|**adPermObjTable**|1|L'oggetto è una tabella.|  
|**adPermObjView**|5|L'oggetto è una vista.|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[Metodo GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[Metodo SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)|[Metodo SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|

