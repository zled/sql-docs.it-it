---
title: ObjectTypeEnum | Documenti Microsoft
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
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10be1fc92c24a074080879fdbcb4ff50892f3840
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Specifica il tipo di oggetto di database per cui impostare le autorizzazioni o la proprietà.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|L'oggetto è una colonna.|  
|**adPermObjDatabase**|3|L'oggetto è un database.|  
|**adPermObjProcedure**|4|L'oggetto è una procedura.|  
|**adPermObjProviderSpecific**|-1|L'oggetto è un tipo definito dal provider. Si verifica un errore se il *ObjectType* parametro **impostato su adPermObjProviderSpecific** e *ID tipo oggetto* non viene fornito.|  
|**adPermObjTable**|1|L'oggetto è una tabella.|  
|**adPermObjView**|5|L'oggetto è una vista.|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[Metodo GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[Metodo SetObjectOwner (ADOX)](../../../ado/reference/adox-api/setobjectowner-method.md)|[Metodo SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
