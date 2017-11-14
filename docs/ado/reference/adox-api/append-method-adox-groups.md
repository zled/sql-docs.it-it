---
title: Append (metodo) (ADOX gruppi) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Groups::raw_Append
- Groups::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 56b94fc6-7ef0-4e4a-82a3-033b94c46036
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed08c3fc0f871c1e7fb8a5885f44390770d4a7a5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-groups"></a>Append (metodo) (ADOX gruppi)
Aggiunge un nuovo [gruppo](../../../ado/reference/adox-api/group-object-adox.md) dell'oggetto per il [gruppi](../../../ado/reference/adox-api/groups-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Parametri  
 *Gruppo*  
 Il **gruppo** oggetto da accodare o il nome del gruppo per creare e aggiungere.  
  
## <a name="remarks"></a>Osservazioni  
 Il **gruppi** raccolta di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) rappresenta tutti gli account di gruppo del catalogo. Il **gruppi** raccolta per un [utente](../../../ado/reference/adox-api/user-object-adox.md) rappresenta solo il gruppo a cui appartiene l'utente.  
  
 Se il provider non supporta la creazione di gruppi, si verificherà un errore.  
  
> [!NOTE]
>  Prima di accodare un **gruppo** dell'oggetto per il **gruppi** raccolta di un **utente** oggetto, un **gruppo** oggetto con lo stesso [ Nome](../../../ado/reference/adox-api/name-property-adox.md) dell'oggetto da aggiungere deve già esistere nel **gruppi** insieme il **catalogo**.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utenti e gruppi, ChangePassword metodi esempio Append (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX procedure)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (metodo) (ADOX utenti)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append (metodo) (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)

