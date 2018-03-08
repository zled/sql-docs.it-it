---
title: Architettura ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e1d59692492b2b14a51a8541e01d5e06a1a6d88
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-architecture"></a>Architettura ODBC
L'architettura ODBC include quattro componenti:  
  
-   **Applicazione** esegue l'elaborazione e chiamate di funzioni ODBC per inviare istruzioni SQL e recuperare risultati.  
  
-   **Gestione driver** carica e scarica i driver per conto di un'applicazione. Funzione ODBC processi chiama o li passa a un driver.  
  
-   **Driver** funzione processi ODBC chiama, invia le richieste SQL di un'origine dati specifica e restituisce i risultati all'applicazione. Se necessario, il driver modifica richiesta di un'applicazione in modo che la richiesta è conforme alla sintassi supportata dal sistema DBMS associato.  
  
-   **Origine dati** Consists dei dati l'utente desidera accedere e il sistema operativo associato, DBMS e piattaforma di rete (se presente) utilizzato per accedere a DBMS.  
  
 Si noti quanto segue sull'architettura ODBC. Possono esistere prima, più i driver e le origini dati, che consente all'applicazione di accedere contemporaneamente ai dati da più di un'origine dati. In secondo luogo, l'API ODBC viene utilizzato in due posizioni: tra l'applicazione e di gestione Driver e tra gestione Driver e tutti i driver. L'interfaccia tra il gestore di Driver e i driver è talvolta detta il *interfaccia del provider del servizio,* o *SPI*. Per ODBC, l'application programming interface (API) e il servizio provider interfaccia sono uguali. vale a dire tutti i driver e gestione Driver hanno la stessa interfaccia per le stesse funzioni.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Applicazioni](../../odbc/reference/applications.md)  
  
-   [Gestione driver](../../odbc/reference/the-driver-manager.md)  
  
-   [Driver](../../odbc/reference/drivers.md)  
  
-   [Origini dati](../../odbc/reference/data-sources.md)
