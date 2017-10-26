---
title: Cronologia dei driver di Database Desktop | Documenti Microsoft
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
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f6876496d243cefd2f3d6b7eb0cd5480bf225189
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="history-of-the-desktop-database-drivers"></a>Cronologia dei driver di Database Desktop
Nella tabella seguente mostra la cronologia delle versioni Desktop driver di Database.  
  
|Versione|Data di rilascio|Description|  
|-------------|------------------|-----------------|  
|1,0|Agosto 1993|Usato il processore di query SIMBA prodotto da PageAhead Software. SIMBA ricevuto chiamate ODBC e istruzioni SQL, li elaborati in chiamate ISAM installabile Microsoft Jet e quindi definito il livello di distribuzione Microsoft Jet ISAM per caricare e chiamare il driver ISAM installabile appropriato.|  
|2.0|Dicembre 1994|Utilizzato con ODBC 2.0, che esteso in modo significativo la funzionalità ODBC. La principale modifica nella versione 2.0 è che il motore di database Microsoft Jet sostituito il processore di query SIMBA. Con il motore di database Microsoft Jet, i driver di Database Desktop molto più strettamente integrato con il driver ISAM installabili Microsoft Jet e tecnologia di Microsoft Access. Sono stati introdotti miglioramenti significativi:<br /><br /> -Supporto per i cursori scorrevoli.<br />-Supporto per gli outer join, i join eterogenei e aggiornabili e transazioni.<br />-versioni a 32 bit dei driver per Microsoft Windows NT.|  
|3.0|Ottobre 1995|Fornisce supporto per Windows 95 e Windows NT Workstation o Server NT 3.51. Solo i driver a 32 bit sono stati inclusi in questa versione. il driver a 16 bit per Windows versione 3.1 sono stati rimossi.|  
|3.5|Ottobre 1996|Questi driver sono stati double byte character set (DBCS)-abilitato, sono state più adatto per l'uso con applicazioni Internet rispetto alle versioni precedenti e inserire l'utilizzo di nomi di origine dati di File (DSN). Il driver Microsoft Access è stato rilasciato in una versione RISC per l'utilizzo su piattaforme Alpha per Windows 95/98 e Windows NT 3.51 e sistemi operativi successivi.|  
|4.0|1998 ad associazione tardiva|Fornisce supporto per il formato Unicode motore Jet di Microsoft insieme compatibilità per le versioni precedenti il formato ANSI.|  
  
> [!NOTE]  
>  I driver version3.5 sono stati progettati per funzionare con ODBC2. *x*. Anche se funzionano anche con ODBC 3.0, non supportano tutte le funzionalità di ODBC 3.0. Per ulteriori informazioni sul funzionano di questi driver con ODBC 3.0, vedere [compatibilità e conformità agli standard](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).

