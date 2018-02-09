---
title: Metodo ChangePassword (ADOX) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 76814245ef5e41e12774df25ea23283f98fd9100
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="changepassword-method-adox"></a>Metodo ChangePassword (ADOX)
Cambia la password per un [utente](../../../ado/reference/adox-api/user-object-adox.md) account.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Parametri  
 *OldPassword*  
 Oggetto **stringa** valore che specifica la password dell'utente esistente. Se l'utente non dispone di una password, utilizzare una stringa vuota ("") per *OldPassword*.  
  
 *NewPassword*  
 Oggetto **stringa** valore che specifica la nuova password.  
  
## <a name="remarks"></a>Osservazioni  
 Per motivi di sicurezza, è necessario specificare la vecchia password oltre la nuova password.  
  
 Se il provider non supporta l'amministrazione delle proprietà trustee, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Append oggetti Group e User, esempio di metodi ChangePassword (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
