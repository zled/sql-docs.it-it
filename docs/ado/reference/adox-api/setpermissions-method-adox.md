---
title: Metodo SetPermissions (ADOX) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cb3bb780109c61b5d481d0d0d3bae56badea819
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286806"
---
# <a name="setpermissions-method-adox"></a>Metodo SetPermissions (ADOX)
Specifica le autorizzazioni per un [gruppo](../../../ado/reference/adox-api/group-object-adox.md) o [utente](../../../ado/reference/adox-api/user-object-adox.md) su un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Oggetto **stringa** valore che specifica il nome dell'oggetto per cui impostare le autorizzazioni.  
  
 *ObjectType*  
 Oggetto **lungo** valore che può essere uno del [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) costanti, che specifica il tipo dell'oggetto per cui ottenere le autorizzazioni.  
  
 *Azione*  
 Oggetto **lungo** valore che può essere uno del [ActionEnum](../../../ado/reference/adox-api/actionenum.md) le costanti che specifica il tipo di azione da eseguire quando si impostano autorizzazioni.  
  
 *Diritti*  
 Oggetto **lungo** valore che può essere una maschera di bit di uno o più di [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) costanti, che indica i diritti per impostare.  
  
 *Ereditare*  
 Facoltativo. Oggetto **lungo** valore che può essere uno del [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) costanti, che specifica il modo in cui gli oggetti ereditano tali autorizzazioni. Il valore predefinito è **adInheritNone**.  
  
 *ObjectTypeId*  
 Facoltativo. Oggetto **Variant** valore che specifica il GUID per un tipo di oggetto provider che non è definito dalla specifica OLE DB. Questo parametro è obbligatorio se *ObjectType* è impostato su **impostato su adPermObjProviderSpecific**; in caso contrario, non viene utilizzato.  
  
## <a name="remarks"></a>Remarks  
 Se il provider non supporta impostazione dei diritti di accesso per gruppi o utenti, si verificherà un errore.  
  
> [!NOTE]
>  Quando si chiama **SetPermissions**, impostazione delle azioni **adAccessRevoke** sovrascrive tutte le impostazioni del *diritti* parametro. Non impostare *azioni* a **adAccessRevoke** se si desidera che i diritti specificati nel *diritti* parametro diventino effettive.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Oggetto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [GetPermissions e metodi SetPermissions (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Metodo GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Proprietà Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
