---
title: Raccolta di utenti (ADOX) | Documenti Microsoft
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
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7a075a12efcf401a5ba2458a90f410b3eb2586b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287230"
---
# <a name="users-collection-adox"></a>Raccolta di utenti (ADOX)
Contiene tutti archiviati [utente](../../../ado/reference/adox-api/user-object-adox.md) gli oggetti di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) o [gruppo](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Remarks  
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
  
-   [Proprietà, metodi ed eventi della raccolta di oggetti User](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GetPermissions e metodi SetPermissions (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Oggetto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
