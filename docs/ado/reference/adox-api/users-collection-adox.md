---
title: Raccolta di utenti (ADOX) | Documenti Microsoft
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
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b9c19df96e66927c6dc5092cd0584f071a3d3b40
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="users-collection-adox"></a>Raccolta di utenti (ADOX)
Contiene tutti archiviati [utente](../../../ado/reference/adox-api/user-object-adox.md) gli oggetti di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) o [gruppo](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Osservazioni  
 Il **utenti** raccolta di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) rappresenta gli utenti del catalogo. Il **utenti** raccolta per un [gruppo](../../../ado/reference/adox-api/group-object-adox.md) rappresenta solo gli utenti appartenenti al gruppo specifico.  
  
 Il [Append](../../../ado/reference/adox-api/append-method-adox-users.md) metodo per un **utenti** insieme è univoco in ADOX. È possibile effettuare le operazioni seguenti:  
  
-   Aggiungere un nuovo utente alla raccolta utilizzando la **Append** metodo.  
  
 Le proprietà e i metodi rimanenti sono standard per le raccolte di ADO. È possibile effettuare le operazioni seguenti:  
  
-   Accedere a un utente nella raccolta con il [elemento](../../../ado/reference/ado-api/item-property-ado.md) proprietà.  
  
-   Restituire il numero di utenti inclusi nella raccolta con il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà.  
  
-   Rimuovere un utente dalla raccolta con il [eliminare](../../../ado/reference/adox-api/delete-method-adox-collections.md) metodo.  
  
-   Aggiornare gli oggetti nella raccolta in base allo schema del database corrente con il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo.  
  
> [!NOTE]
>  Prima di accodare un **utente** dell'oggetto per il **utenti** raccolta di un **gruppo** oggetto, un **utente** oggetto con lo stesso [nome ](../../../ado/reference/adox-api/name-property-adox.md) dell'oggetto da aggiungere deve già esistere nel **utenti** insieme il **catalogo**.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà di raccolta di utenti, metodi ed eventi](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GetPermissions e metodi SetPermissions (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Oggetto utente (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)

