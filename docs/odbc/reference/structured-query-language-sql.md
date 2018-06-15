---
title: Structured Query Language (SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e28770a1532d8d52ec8069d00154c4b377628d1f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916633"
---
# <a name="structured-query-language-sql"></a>Structured Query Language (SQL)
Un tipico DBMS consente agli utenti di archiviare, accedere e modificare i dati in modo efficiente, organizzato. Gli utenti del DBMS erano originariamente, i programmatori. Accesso ai dati archiviati, è necessario scrivere un programma in un linguaggio di programmazione, ad esempio COBOL. Mentre questi programmi sono stati scritti spesso per presentare un'interfaccia a un utente tecniche, i servizi di esperti programmatori necessario l'accesso ai dati. Accesso casuale ai dati non è pratico.  
  
 Gli utenti non sono del tutto soddisfatti questa situazione. Mentre è stato possibile accedere ai dati, è spesso necessario convincere un programmatore DBMS per scrivere un software speciale. Ad esempio, se un reparto vendite desidera visualizzare le vendite totali del mese precedente da ognuno dei relativi agenti e di voleva queste informazioni classificate in ordine per lunghezza di ogni venditore del servizio della società, si sono disponibili due opzioni: entrambi un programma che esiste già le informazioni a cui accedere in questo modo è consentito o il reparto era necessario chiedere a un programmatore di scrivere un programma. In molti casi, questo è più attività si vale la pena ed era sempre una soluzione costosa per le richieste occasionale o ad hoc. Come accedere facilmente agli utenti più anche questo problema è di grandi dimensioni.  
  
 Consentendo agli utenti di accedere ai dati in base ad hoc, è necessario assegnare loro una lingua in cui esprimere le proprie richieste. Una singola richiesta a un database viene definita come una query. un linguaggio di questo tipo viene chiamato un linguaggio di query. Molti linguaggi di query sono stati sviluppati per questo scopo, ma uno di questi è diventato più diffusi: Structured Query Language, inventati IBM nel 1970s. È comunemente noto relativo un acronimo, SQL e si pronuncia "ess-cue-ell" sia come "seguito"; questo manuale viene utilizzata la pronuncia precedente. SQL è diventato ANSI standard nel 1986 e un file ISO standard nel 1987; viene usato attualmente in una grande molti sistemi di gestione di database.  
  
 Sebbene SQL consente di risolvere le esigenze degli utenti ad hoc, la necessità di accesso ai dati per programmi per computer non più visualizzato. In effetti, la maggior parte delle accesso al database ancora (e) a livello di codice, sotto forma di report pianificati regolarmente e analisi statistiche, i programmi di immissione di dati, ad esempio quelli usati per ordini e dati programmi di modifica, ad esempio quelli utilizzati per risolvere le differenze tra gli account e generare gli ordini di lavoro.  
  
 Questi programmi anche usare SQL, utilizzando uno dei tre tecniche seguenti:  
  
-   **Embedded SQL**, in SQL le istruzioni vengono incorporate in un linguaggio host quale C o COBOL.  
  
-   **I moduli SQL**, quali istruzioni SQL vengono compilate nel sistema DBMS e chiamate da un linguaggio host.  
  
-   **Chiamata a livello di interfaccia**, o CLI, costituito dalle funzioni chiamate per passare le istruzioni SQL per il sistema DBMS e recuperare i risultati da DBMS.  
  
> [!NOTE]  
>  È un fatto che il termine chiamata a livello di interfaccia viene utilizzata invece di programmazione di applicazioni dell'interfaccia (API), un altro termine per la stessa cosa. Nel mondo, database API viene usata per descrivere SQL stesso: SQL è l'API per un sistema DBMS.  
  
 Di queste opzioni, embedded SQL è più comunemente utilizzate, sebbene la maggior parte dei principali DBMS supportare CLI di proprietari.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Elaborazione di un'istruzione SQL](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [Moduli SQL](../../odbc/reference/sql-modules.md)  
  
-   [Call-Level Interface](../../odbc/reference/call-level-interfaces.md)
