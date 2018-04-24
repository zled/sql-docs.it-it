---
title: Metodo GetObjectOwner (ADOX) | Documenti Microsoft
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
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 794778d24a33a9d7475e19abe6ed577c3c49b370
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="getobjectowner-method-adox"></a>Metodo GetObjectOwner (ADOX)
Restituisce il proprietario di un oggetto in un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **stringa** valore che specifica il [nome](../../../ado/reference/adox-api/name-property-adox.md) del [utente](../../../ado/reference/adox-api/user-object-adox.md) o [gruppo](../../../ado/reference/adox-api/group-object-adox.md) che possiede l'oggetto.  
  
#### <a name="parameters"></a>Parametri  
 *ObjectName*  
 Oggetto **stringa** valore che specifica il nome dell'oggetto per cui restituire il proprietario.  
  
 *ObjectType*  
 Oggetto **lungo** valore che può essere uno del [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) costanti, che specifica il tipo dell'oggetto per cui ottenere il proprietario.  
  
 *ObjectTypeId*  
 Facoltativa. Oggetto **Variant** valore che specifica il GUID per un tipo di oggetto del provider non definito dalla specifica OLE DB. Questo parametro è obbligatorio se *ObjectType* è impostato su **impostato su adPermObjProviderSpecific**; in caso contrario, non viene utilizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Se il provider non supporta la restituzione dei proprietari degli oggetti, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GetObjectOwner e metodi SetObjectOwner (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Metodo SetObjectOwner (ADOX)](../../../ado/reference/adox-api/setobjectowner-method.md)
