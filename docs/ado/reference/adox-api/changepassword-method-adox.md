---
title: Metodo ChangePassword (ADOX) | Documenti Microsoft
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
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 18dd53bc701cf6a4b77c8e77f5b1851aff57f2ba
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
 [Oggetto utente (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utenti e gruppi, ChangePassword metodi esempio Append (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
