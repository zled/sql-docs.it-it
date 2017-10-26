---
title: Utilizzando l'autenticazione del sistema operativo | Documenti Microsoft
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
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3fbe8f4ce9fe9edbb88c7c895311bd9560dc28f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-operating-system-authentication"></a>Utilizzando l'autenticazione del sistema operativo
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Autenticazione del sistema operativo Oracle si basa sul sistema operativo sottostante per controllare l'accesso agli account di database. Gli utenti non devono immettere una password quando si utilizza questo tipo di account di accesso.  
  
 Per sfruttare i vantaggi di questa funzionalità, specificare "/" come l'ID utente e non si specifica una password quando ci si connette usando una qualsiasi delle API di connessione seguente: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), o [ SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Utilizzano di database Oracle SQL * Net i servizi di autenticazione per autenticare gli utenti connessi. Questo servizio funziona anche se gli utenti sono connessi in Oracle mediante SQLPlus; Tuttavia, quando l'utente connesso è un servizio, ad esempio Internet Information Services, l'autenticazione ha esito negativo. Si tratta di una limitazione nota del SQL\*autenticazione Net e produce il seguente errore: "[Microsoft] [driver ODBC per Oracle] [Oracle] ORA-12641: Impossibile inizializzare il servizio TNS:authentication."  
  
 È possibile correggere il problema modificando il file Sqlnet.ora. Questo file di configurazione verrà in genere archiviato nella sottodirectory Network\Admin della home directory Oracle. Aggiungere la riga seguente Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```

