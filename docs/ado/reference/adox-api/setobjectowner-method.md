---
title: Metodo SetObjectOwner | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 33226468d9d1f556d2cf7ec3edac37375b0c8d84
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setobjectowner-method"></a>Metodo SetObjectOwner
Specifica il proprietario di un oggetto in un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parametri  
 *ObjectName*  
 Oggetto **stringa** valore che specifica il nome dell'oggetto per cui si desidera specificare il proprietario.  
  
 *ObjectType*  
 Oggetto **lungo** valore che può essere uno del [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) costanti che specifica il tipo di proprietario.  
  
 *OwnerName*  
 Oggetto **stringa** valore che specifica il [nome](../../../ado/reference/adox-api/name-property-adox.md) del [utente](../../../ado/reference/adox-api/user-object-adox.md) o [gruppo](../../../ado/reference/adox-api/group-object-adox.md) proprietario dell'oggetto.  
  
 *ID tipo oggetto*  
 Facoltativa. Oggetto **Variant** valore che specifica il GUID per un tipo di oggetto provider che non è definito dalla specifica OLE DB. Questo parametro è obbligatorio se *ObjectType* è impostato su **impostato su adPermObjProviderSpecific**; in caso contrario, non viene utilizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Se il provider non supporta specificando i proprietari degli oggetti, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GetObjectOwner e metodi SetObjectOwner (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Metodo GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
