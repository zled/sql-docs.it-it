---
title: Metodo GetObjectOwner (ADOX) | Documenti Microsoft
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
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3c6f6aa4401646f43dd303988cc151d1ed43d21
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
  
 *ID tipo oggetto*  
 Facoltativa. Oggetto **Variant** valore che specifica il GUID per un tipo di oggetto del provider non definito dalla specifica OLE DB. Questo parametro è obbligatorio se *ObjectType* è impostato su **impostato su adPermObjProviderSpecific**; in caso contrario, non viene utilizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Se il provider non supporta la restituzione dei proprietari degli oggetti, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GetObjectOwner e metodi SetObjectOwner (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Metodo SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)
