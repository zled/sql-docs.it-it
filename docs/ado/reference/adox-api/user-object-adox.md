---
title: Oggetto utente (ADOX) | Documenti Microsoft
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
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3565b06fa33ddf0990b89724639d9538da37e9b6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="user-object-adox"></a>Oggetto utente (ADOX)
Rappresenta un account utente che dispone delle autorizzazioni di accesso all'interno di un database protetto.  
  
## <a name="remarks"></a>Osservazioni  
 Il [utenti](../../../ado/reference/adox-api/users-collection-adox.md) raccolta di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) rappresenta gli utenti del catalogo. Il **utenti** raccolta per un [gruppo](../../../ado/reference/adox-api/group-object-adox.md) rappresenta solo gli utenti del gruppo specifico.  
  
 Con la proprietà, raccolte e i metodi di un **utente** dell'oggetto, è possibile:  
  
-   Identificare l'utente con il [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Modificare la password per un utente con il [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) metodo.  
  
-   Determinare se un utente disponga di lettura, scrittura o eliminazione di autorizzazioni con il [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) e [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) metodi.  
  
-   Accedere ai gruppi a cui appartiene un utente con il [gruppi](../../../ado/reference/adox-api/groups-collection-adox.md) insieme.  
  
-   Accedere a proprietà specifiche del provider con il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
-   Determinare il [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) per un utente.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà dell'oggetto utente, metodi ed eventi](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GetPermissions e metodi SetPermissions (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Raccolta di utenti (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)

