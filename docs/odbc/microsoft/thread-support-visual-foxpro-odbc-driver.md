---
title: Thread di supporto (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cd540c727f1e8a77dbb6d8201715c213ff688909
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Supporto dei thread, Driver ODBC di Visual FoxPro,
Il Driver ODBC di Visual FoxPro è thread-safe. Accesso a handle di ambiente (*uando*), gli handle di connessione (*hdbc*) e gli handle di istruzione (*hstmt*) viene eseguito il wrapping in semafori appropriati per impedire ad altri processi l'accesso e potenzialmente la modifica di strutture di dati interne del driver.  
  
 In un'applicazione multithreading, è possibile annullare una funzione che è in esecuzione in modo sincrono su un *hstmt* chiamando [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) in un thread separato.  
  
 Il driver utilizza un thread separato per recuperare i dati quando si utilizza il recupero di massa progressivo. Per utilizzare il recupero di massa progressivo per un'origine dati, selezionare il **recuperare i dati in background** casella di controllo di [la finestra di dialogo di installazione di ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) o utilizzare la parola chiave attributo BackgroundFetch nella connessione stringa. Evitare l'utilizzo di recupero in background quando si chiama il driver da applicazioni multithreading. Per informazioni sulle parole chiave di attributo stringa di connessione, vedere [utilizzando le stringhe di connessione](../../odbc/microsoft/using-connection-strings.md).  
  
 Per ulteriori informazioni sui thread e **SQLCancel**, vedere [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) nel *riferimento per programmatori ODBC*.
