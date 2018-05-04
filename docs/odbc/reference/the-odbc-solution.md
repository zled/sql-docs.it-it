---
title: La soluzione ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], using ODBC
ms.assetid: 34b80790-e010-4b90-8eaa-03189f5d8986
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f028b4e452f1318f7f0142f7b41e06fc8ced368
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="the-odbc-solution"></a>La soluzione ODBC
La domanda, quindi, è come ODBC standardizzare accesso al database? Esistono due requisiti di architettura:  
  
-   Applicazioni devono essere in grado di accedere più DBMS utilizzando lo stesso codice sorgente senza dover ricompilare o ricollegamento.  
  
-   Applicazioni devono essere in grado di accedere contemporaneamente a più DBMS.  
  
 Se è una domanda più, a causa di realtà marketplace:  
  
-   Le funzionalità DBMS deve esporre ODBC? Solo le funzionalità comuni a tutti i DBMS o tutte le funzionalità che sono disponibile in qualsiasi sistema DBMS?  
  
 ODBC risolve questi problemi nel modo seguente:  
  
-   **ODBC è un'interfaccia a livello di chiamata.** Per risolvere il problema della modalità di accesso più DBMS utilizzando lo stesso codice di origine da parte di applicazioni, ODBC definisce standard CLI. Contiene tutte le funzioni nelle specifiche CLI da Open Group e ISO/IEC e fornisce funzioni aggiuntive comunemente richieste dalle applicazioni.  
  
     Libreria diverso, un driver, è necessario per ogni sistema DBMS che supporti ODBC. Il driver implementa le funzioni dell'API ODBC. Per utilizzare un driver diverso, l'applicazione non è necessario essere ricompilate o ricollegate. In alternativa, semplicemente l'applicazione carica il driver nuovo e chiama le funzioni. Per accedere contemporaneamente a più DBMS, l'applicazione carica più driver. La modalità in cui sono supportati i driver è specifico del sistema operativo. Nel sistema operativo Microsoft® Windows®, ad esempio, i driver sono librerie a collegamento dinamico (DLL).  
  
-   **ODBC definisce una grammatica SQL standard.** Oltre a un'interfaccia a livello di chiamata standard, ODBC definisce una grammatica SQL standard. Questa grammatica è basata sulla specifica Open CAE SQL di gruppo. Differenze tra le due grammatiche sono minime e principalmente a causa delle differenze tra la grammatica SQL richiesto da incorporate CLI (ODBC) e SQL (Open Group). Esistono inoltre alcune estensioni per la grammatica per esporre le funzionalità del linguaggio disponibili in genere non coperto dalla grammatica Open Group.  
  
     Le applicazioni possono inviare le istruzioni che utilizzano ODBC o specifici del DBMS di grammatica. Se un'istruzione utilizza grammatica ODBC che è diversa dalla grammatica specifici del DBMS, il driver converte prima dell'invio all'origine dati. Tuttavia, queste conversioni sono rare, poiché la maggior parte dei DBMS già in uso la grammatica SQL standard.  
  
-   **ODBC fornisce una gestione Driver per gestire l'accesso simultaneo a più DBMS.** Sebbene l'utilizzo di driver risolve il problema dell'accesso a più DBMS contemporaneamente, è possibile che il codice per eseguire questa operazione può essere complesso. Le applicazioni che vengono progettate per funzionare con tutti i driver non possono essere collegate staticamente per tutti i driver. Ma è necessario caricare i driver in fase di esecuzione e chiamare le funzioni in essi contenuti tramite una tabella di puntatori a funzione. La situazione diventa più complessa se l'applicazione usa più driver contemporaneamente.  
  
     Anziché richiedere ogni applicazione a tale scopo, ODBC offre una gestione Driver. Gestione Driver implementa tutte le funzioni ODBC, principalmente come pass-through chiamate a funzioni ODBC driver e in modo statico è collegata all'applicazione o caricate dall'applicazione in fase di esecuzione. Di conseguenza, l'applicazione chiama funzioni ODBC in base al nome in Gestione Driver, anziché dal puntatore in tutti i driver.  
  
     Quando un'applicazione richiede un driver specifico, innanzitutto richiede un handle di connessione da utilizzare per identificare i driver e le richieste di gestione Driver caricare il driver. Gestione Driver viene caricato il driver e archivia l'indirizzo di ogni funzione nel driver. Per chiamare una funzione ODBC nel driver, l'applicazione chiama tale funzione in Gestione Driver e passa l'handle di connessione per il driver. Gestione Driver quindi chiama la funzione utilizzando l'indirizzo memorizzate in precedenza.  
  
-   **ODBC espone un numero significativo di funzionalità DBMS, ma non hanno bisogno di driver per supportare tutti gli elementi.** Se ODBC esposte solo le funzionalità che sono comuni a tutti i DBMS, sarebbe di grande utilità; Dopo tutto, il motivo, in modo DBMS diversi più attualmente esistenti è che dispongono di funzionalità diversi. Se ODBC esposte tutte le funzionalità che sono disponibile in qualsiasi sistema DBMS, sarebbe impossibile per implementare i driver.  
  
     Invece ODBC espone un numero significativo di funzionalità, più sono supportati da DBMS la maggior parte, ma richiede driver di implementare solo un subset di tali funzionalità. I driver di implementano le funzionalità rimanenti solo se sono supportate dal sistema DBMS sottostante o se si sceglie di emulare li. Di conseguenza, le applicazioni possono essere scritti per sfruttare le funzionalità di un singolo DBMS esposto dal driver per DBMS, per utilizzare solo le funzionalità utilizzate da tutti i DBMS, o per verificare il supporto di una particolare funzionalità e reagire di conseguenza.  
  
     In modo che un'applicazione può determinare quali funzionalità di un driver e il supporto di DBMS, ODBC fornisce due funzioni (**SQLGetInfo** e **SQLGetFunctions**) che restituiscono informazioni generali sui driver e DBMS funzionalità e un elenco di funzioni il driver supporta. Anche ODBC definisce API e SQL grammatica livelli di conformità, che specificano intervalli ampia di funzionalità supportate dal driver. Per ulteriori informazioni, vedere [livelli di conformità](../../odbc/reference/develop-app/conformance-levels.md).  
  
     È importante ricordare che ODBC definisce un'interfaccia comune per tutte le funzionalità che espone. Per questo motivo, le applicazioni contengono codice specifiche funzionalità, non il codice specifico DBMS e possono utilizzare tutti i driver che espongono le funzionalità. Un vantaggio consiste nel fatto che le applicazioni non dovranno essere aggiornati quando vengono migliorate le funzionalità supportate da un DBMS; al contrario, quando viene installato un driver aggiornato, l'applicazione utilizza automaticamente le funzionalità perché il relativo codice specifiche funzionalità, non è specifico del driver o specifici del DBMS.
