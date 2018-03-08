---
title: ODBC e Standard CLI | Documenti Microsoft
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
- ODBC [ODBC], CLI
- CLI [ODBC]
- CLI [ODBC], about CLI
- call-level interface [ODBC]
- call-level interface [ODBC], about call-level interface
ms.assetid: 79b9c268-16ac-4b80-b451-f9dcd8c02ca4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8133a266e81a1711947af9acb34a89b861a32b16
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-the-standard-cli"></a>ODBC e Standard CLI
ODBC in linea con le seguenti specifiche standard in grado di gestire con interfaccia a livello di chiamata (CLI). (Le funzioni ODBC sono un superset di ognuno di questi standard).  
  
-   La specifica di CAE Open Group "Data Management: SQL a livello di chiamata interfaccia (CLI)"  
  
-   ISO/IEC 9075-interfaccia a livello di chiamata 3:1995 (E) (SQL/CLI)  
  
 Come risultato l'allineamento, in quanto si verifica quanto segue:  
  
-   Un'applicazione scritta per le specifiche di ISO CLI Open Group funziona con un'applicazione ODBC 3. *x* driver o un driver conforme agli standard quando viene compilato con ODBC 3. *x* i file di intestazione e collegate con ODBC 3. *x* librerie, e quando accede al driver tramite ODBC 3. *x* gestione Driver.  
  
-   Un driver di scrivere le specifiche Open Group e ISO CLI funzionerà con un'applicazione ODBC 3*x* o come applicazione conforme agli standard quando viene compilato con ODBC 3*x* file di intestazione e collegati con ODBC 3*x* librerie, e quando l'applicazione accede al driver tramite ODBC 3*x* gestione Driver. (Per ulteriori informazioni, vedere [conforme agli standard di applicazioni e driver](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Il livello di conformità di interfaccia di base include tutte le funzionalità CLI ISO e tutte le funzionalità necessari in CLI gruppo aperto. Funzionalità facoltative di CLI Apri gruppo vengono visualizzati in più livelli di conformità di interfaccia. Poiché tutti ODBC 3. *x* driver sono necessari per supportare le funzionalità del livello di conformità interfaccia principale, vengono soddisfatte le seguenti:  
  
-   Un database ODBC 3. *x* driver supporterà tutte le funzionalità utilizzate da un'applicazione conforme agli standard.  
  
-   Un database ODBC 3. *x* applicazione usando solo le funzionalità di CLI ISO e le funzionalità necessari di CLI gruppo aperto funzionerà con qualsiasi driver conforme agli standard.  
  
 Oltre alle specifiche di chiamata a livello di interfaccia contenute negli standard ISO/IEC e Apri gruppo CLI ODBC implementa le funzionalità seguenti. (Alcune di queste funzionalità disponibili nelle versioni di ODBC prima ODBC 3. *x*.)  
  
-   Operazioni di recupero su più righe da una sola chiamata di funzione  
  
-   Associazione a una matrice di parametri  
  
-   Supporto per segnalibro inclusi il recupero dal segnalibro, a lunghezza variabile segnalibri e delle operazioni bulk, aggiornamento ed eliminazione da operazioni di segnalibro nelle righe non contigue  
  
-   Associazione per riga  
  
-   Offset di associazione  
  
-   Supporto per i batch di istruzioni SQL, in una stored procedure o come una sequenza di istruzioni SQL eseguite tramite **SQLExecute** o **SQLExecDirect**  
  
-   Conteggio delle righe di cursore esatto o approssimativo  
  
-   Trova aggiornamento e le operazioni di eliminazione e batch di aggiornamenti ed eliminazioni, chiamata di funzione (**SQLSetPos**)  
  
-   Funzioni di catalogo che estrarre informazioni dallo schema di informazioni senza la necessità di viste degli schemi delle informazioni di supporto  
  
-   Sequenze di escape per l'outer join, funzioni scalari, valori letterali datetime, valori letterali di intervallo e le stored procedure  
  
-   Librerie di conversione tabella codici  
  
-   Creazione di report di supporto di SQL e il livello di conformità ANSI di un driver  
  
-   Popolamento automatico su richiesta del descrittore del parametro di implementazione  
  
-   Diagnostica avanzata e le matrici di stato di riga e di parametro  
  
-   DateTime, intervallo, numerici o decimali e tipi di buffer dell'applicazione a 64 bit  
  
-   Esecuzione asincrona  
  
-   Supporto delle stored procedure, incluse le sequenze di escape, meccanismi di associazione di parametro di output e funzioni di catalogo  
  
-   Miglioramenti di connessione includono il supporto per gli attributi di connessione e l'esplorazione di attributo
