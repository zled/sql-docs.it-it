---
title: Gruppi di raccolta (ADOX) | Documenti Microsoft
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
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3dfb8a9e2f75fb11caf64b06e34016474d7b9fa7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="groups-collection-adox"></a>Raccolta di gruppi (ADOX)
Contiene tutti archiviati [gruppo](../../../ado/reference/adox-api/group-object-adox.md) gli oggetti di un catalogo o un utente.  
  
## <a name="remarks"></a>Osservazioni  
 Il **gruppi** raccolta di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) rappresenta tutti gli account di gruppo del catalogo. Il **gruppi** raccolta per un [utente](../../../ado/reference/adox-api/user-object-adox.md) rappresenta solo il gruppo a cui appartiene l'utente.  
  
 Il [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) metodo per un **gruppi** insieme è univoco in ADOX. È possibile effettuare le operazioni seguenti:  
  
-   Aggiungere un nuovo gruppo di sicurezza alla raccolta con il **Append** metodo.  
  
 Le proprietà e i metodi rimanenti sono standard per le raccolte di ADO. È possibile effettuare le operazioni seguenti:  
  
-   Accedere a un gruppo nella raccolta con il [elemento](../../../ado/reference/ado-api/item-property-ado.md) proprietà.  
  
-   Restituire il numero di gruppi contenuti nella raccolta con il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà.  
  
-   Rimuovere un gruppo dalla raccolta con il [eliminare](../../../ado/reference/adox-api/delete-method-adox-collections.md) metodo.  
  
-   Aggiornare gli oggetti nella raccolta in modo da riflettere lo schema del database corrente con il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo.  
  
> [!NOTE]
>  Prima di accodare un **gruppo** dell'oggetto per il **gruppi** raccolta di un **utente** oggetto, un **gruppo** oggetto con lo stesso [ Nome](../../../ado/reference/adox-api/name-property-adox.md) dell'oggetto da aggiungere deve già esistere nel **gruppi** insieme il **catalogo**.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà di raccolta di gruppi, metodi ed eventi](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Oggetto di gruppo (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
