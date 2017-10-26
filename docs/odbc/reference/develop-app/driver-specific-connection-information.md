---
title: Informazioni di connessione specifici del driver | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLConnect function [ODBC], driver-specific connection information
- connecting to driver [ODBC], SQLConnect
- SQLDriverConnect function [ODBC], driver specific connection information
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SQLConnect
- connecting to driver [ODBC], driver-specific information
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9e1624febc9b53c654c1b01f5aafb601b97b3cbf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="driver-specific-connection-information"></a>Informazioni di connessione specifici del driver
**SQLConnect** si presuppone che un nome dell'origine dati, l'ID utente e password siano sufficienti per connettersi a un'origine dati e che tutte le altre informazioni di connessione possono essere archiviate nel sistema. Non si tratta spesso il caso. Ad esempio, un driver potrebbe essere necessario un ID utente e password per accedere a un server e un ID utente diverso e una password per accedere a un sistema DBMS. Poiché **SQLConnect** accetta un ID utente singolo e una password, ciò significa che l'altro ID utente e password devono essere archiviati con le informazioni di origine dati nel sistema se **SQLConnect** deve essere utilizzato. Si tratta di una potenziale violazione della sicurezza e deve essere evitato, a meno che la password è crittografata.  
  
 **SQLDriverConnect** consente al driver di definire una quantità arbitraria di informazioni di connessione nelle coppie valore-parola chiave della stringa di connessione. Si supponga, ad esempio, che un driver richiede un nome origine dati, un ID utente e una password per il server e un ID utente e una password per il sistema DBMS. Un programma personalizzato che utilizza sempre l'origine dati XYZ Corp potrebbe richiedere all'utente per l'ID e password e compilare il seguente set di coppie valore-parola chiave, o *stringa di connessione,* per passare a **SQLDriverConnect**:  
  
> [!NOTE]  
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare `Trusted_Connection=yes` anziché informazioni utente ID e password nella stringa di connessione.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Il **DSN** (parola chiave) (nome dell'origine dati) indica l'origine dati, il **UID** e **PWD** parole chiave specificano l'ID utente e password per il server e **UIDDBMS ** e **PWDDBMS** parole chiave specificano l'ID utente e password per il sistema DBMS. Si noti che il punto e virgola finale è facoltativo. **SQLDriverConnect** analizza la stringa; utilizza il nome dell'origine dati XYZ Corp per recuperare le informazioni di connessione aggiuntive dal sistema, ad esempio l'indirizzo del server; e accede al server e DBMS utilizzando l'ID utente specificato e una password.  
  
 Le coppie parola chiave / valore **SQLDriverConnect** deve seguire determinate regole di sintassi. Le parole chiave e i relativi valori non devono contenere il **[] {} (),? \*=! @** caratteri. Il valore di **DSN** parola chiave non può essere costituito solo da spazi vuoti e non deve contenere spazi vuoti iniziali. A causa di grammatica del Registro di sistema, i nomi delle origini dati e le parole chiave non può contenere la barra rovesciata (\\) caratteri. Racchiudere il segno di uguale nella coppia valore-parola chiave non sono consentiti spazi.  
  
 Il **FILEDSN** parola chiave può essere utilizzata in una chiamata a **SQLDriverConnect** per specificare il nome di un file che contiene informazioni sull'origine dati (vedere [la connessione utilizzando le origini dati](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), più avanti in questa sezione). Il **SAVEFILE** (parola chiave) consente di specificare il nome di un file DSN in cui le coppie parola chiave / valore di una connessione ha esito positivo eseguite dalla chiamata a **SQLDriverConnect** verranno salvate. Per ulteriori informazioni sulle origini dati di file, vedere il [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.

