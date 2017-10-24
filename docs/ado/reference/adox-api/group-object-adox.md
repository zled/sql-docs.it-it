---
title: Gruppo di oggetti (ADOX) | Documenti Microsoft
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
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 16aad2cd94a457d3d6efe97326fdbe7e6c06e53d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="group-object-adox"></a>Oggetto di gruppo (ADOX)
Rappresenta un account di gruppo che dispone delle autorizzazioni di accesso all'interno di un database protetto.  
  
## <a name="remarks"></a>Osservazioni  
 Il [gruppi](../../../ado/reference/adox-api/groups-collection-adox.md) raccolta di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) rappresenta gli account di gruppo del catalogo. Il **gruppi** raccolta per un [utente](../../../ado/reference/adox-api/user-object-adox.md) rappresenta solo il gruppo a cui appartiene l'utente.  
  
 Con la proprietà, raccolte e i metodi di un **gruppo** dell'oggetto, è possibile:  
  
-   Identificare il gruppo con il [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Determinare se un gruppo dispone di lettura, scrittura o eliminazione di autorizzazioni con il [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) e [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) metodi.  
  
-   Accesso agli account utente che dispongono di appartenenze nel gruppo con il [utenti](../../../ado/reference/adox-api/users-collection-adox.md) insieme.  
  
-   Accedere a proprietà specifiche del provider con il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Gruppo di proprietà, metodi ed eventi](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Raccolta di utenti (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)

