---
title: Informazioni di connessione specifici del driver | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConnect function [ODBC], driver-specific connection information
- connecting to driver [ODBC], SQLConnect
- SQLDriverConnect function [ODBC], driver specific connection information
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SQLConnect
- connecting to driver [ODBC], driver-specific information
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3852e713e517828e83e74bf7fb291ef20865532
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797232"
---
# <a name="driver-specific-connection-information"></a>Informazioni di connessione specifiche del driver
**SQLConnect** presuppone che un nome dell'origine dati, l'ID utente e password siano sufficienti per connettersi a un'origine dati e che tutte le altre informazioni di connessione possono essere archiviati nel sistema. Non si tratta spesso il caso. Ad esempio, un driver potrebbe essere necessario un ID utente e password per accedere a un server e un ID utente diverso e una password per accedere a un sistema DBMS. In quanto **SQLConnect** accetta un ID singolo utente e una password, ciò significa che l'altro ID utente e password devono essere archiviati con le informazioni di origine dati nel sistema se **SQLConnect** deve essere utilizzato. Si tratta di una potenziale violazione della sicurezza e deve essere evitata, a meno che la password viene crittografata.  
  
 **SQLDriverConnect** consente al driver definire un quantità arbitraria di informazioni di connessione nelle coppie valore-parola chiave della stringa di connessione. Si supponga, ad esempio, che un driver richiede un nome dell'origine dati, un ID utente e una password per il server e un ID utente e una password per il sistema DBMS. Un programma personalizzato che utilizza sempre l'origine dati Corp XYZ potrebbe richiedere all'utente per gli ID e password e compilare il seguente set di coppie valore-parola chiave, oppure *stringa di connessione* per passare a **SQLDriverConnect**:  
  
> [!NOTE]  
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare `Trusted_Connection=yes` anziché le informazioni utente di ID e la password nella stringa di connessione.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Il **DSN** parola chiave (Data Source Name) indica l'origine dati, il **UID** e **PWD** parole chiave specificano l'ID utente e password per il server e il **UIDDBMS**  e **PWDDBMS** parole chiave specificano l'ID utente e password per il sistema DBMS. Si noti che il punto e virgola finale è facoltativo. **SQLDriverConnect** analizza questa stringa; Usa il nome dell'origine dati XYZ Corp per recuperare le informazioni di connessione aggiuntive dal sistema, ad esempio l'indirizzo del server; e accede al server e al sistema DBMS con l'ID utente specificato e una password.  
  
 Coppie parola chiave / valore **SQLDriverConnect** devono rispettare determinate regole di sintassi. Le parole chiave e i relativi valori non devono contenere il **[]{}(),? \*=! @** caratteri. Il valore della **DSN** parola chiave non può essere costituito solo da spazi vuoti e non deve contenere spazi vuoti iniziali. A causa la grammatica del Registro di sistema, i nomi delle origini dati e le parole chiave non può contenere la barra rovesciata (\\) caratteri. Non sono consentiti spazi prima e dopo il segno di uguale nella coppia parola chiave / valore.  
  
 Il **FILEDSN** parola chiave può essere utilizzata in una chiamata a **SQLDriverConnect** per specificare il nome di un file che contiene informazioni sull'origine dati (vedere [la connessione con origini dati dei File](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)più avanti in questa sezione). Il **SAVEFILE** parola chiave consente di specificare il nome di un file DSN in cui le coppie parola chiave / valore di una connessione riuscita effettuata dalla chiamata al metodo **SQLDriverConnect** verrà salvato. Per altre informazioni sulle origini dati dei file, vedere la [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.
