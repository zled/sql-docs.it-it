---
title: ODBC Programmer ' &#39; riferimento s | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ODBC [ODBC], reference
ms.assetid: b33c3c43-ae66-44a3-be17-9cd82624dd96
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3fc868b66f6322d9769176671c8df2913d58150e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-programmer39s-reference"></a>ODBC Programmer ' &#39; s riferimento
Il *riferimento per programmatori ODBC* include le sezioni seguenti.  
  
-   [Novità di ODBC 3.8](../../odbc/reference/what-s-new-in-odbc-3-8.md) sono elencate le nuove funzionalità ODBC che sono stati aggiunti in Windows 8 SDK.  
  
-   [Esempio ODBC programma](../../odbc/reference/sample-odbc-program.md) presenta un programma di esempio ODBC.  
  
-   [Introduzione a ODBC](../../odbc/reference/introduction-to-odbc.md) fornisce una breve storia di Structured Query Language e ODBC e le informazioni di carattere generale sull'interfaccia ODBC.  
  
-   [Sviluppo di applicazioni](../../odbc/reference/develop-app/developing-applications.md) contiene informazioni sullo sviluppo di applicazioni che utilizzano l'interfaccia ODBC e driver che l'implementano.  
  
-   [Installazione e configurazione Software ODBC](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) fornisce informazioni sull'installazione e un programma di installazione di riferimento alle funzioni DLL.  
  
-   [Sviluppo di un Driver ODBC](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) contiene informazioni sulla scrittura di un driver.  
  
-   [Riferimento all'API](../../odbc/reference/syntax/odbc-reference.md) contiene la sintassi e semantiche informazioni per tutte le funzioni ODBC.  
  
-   [Appendici ODBC](../../odbc/reference/appendixes/odbc-appendixes.md) contengono dettagli tecnici e fanno riferimento a tabelle di codici di errore ODBC, tipi di dati e la grammatica SQL.  
  
## <a name="working-with-the-odbc-documentation"></a>Utilizzo con la documentazione di ODBC  
 L'interfaccia ODBC è progettato per l'utilizzo con il linguaggio di programmazione C. Utilizzo dell'interfaccia ODBC si estende su tre aree: istruzioni SQL, ODBC chiamate di funzione e programmazione C. Questa documentazione si presuppone quanto segue:  
  
-   Una conoscenza del linguaggio di programmazione C.  
  
-   Una conoscenza generale DBMS e una certa familiarità con SQL.  
  
 Le seguenti convenzioni tipografiche vengono utilizzate.  
  
|Formato|Utilizzo|  
|------------|--------------|  
|SELEZIONARE * DA|Lettere maiuscole indicano le istruzioni SQL, i nomi delle macro e termini utilizzati a livello di comando del sistema operativo.|  
|`RETCODE SQLFetch(hdbc)`|Il tipo di carattere a spaziatura fissa viene utilizzato per le righe di comando di esempio e il codice programma.|  
|*argomento*|Le parole in corsivo indicano gli argomenti a livello di codice, informazioni che l'utente o l'applicazione deve fornire o word enfasi.|  
|**SQLEndTran**|Grassetto indica che la sintassi deve essere digitata esattamente come indicato, inclusi i nomi di funzione.|  
|&#124;|Una barra verticale separa le due opzioni si escludono a vicenda in una riga di sintassi.|  
|...|I puntini di sospensione indica che gli argomenti possono essere ripetuti più volte.|  
|. . .|Una colonna di tre punti indica mantenimento delle righe di codice precedenti.|  
  
## <a name="about-the-code-examples"></a>Informazioni sugli esempi di codice  
 Gli esempi di codice in questa guida sono progettati per solo scopo illustrativo. Poiché sono formulate principalmente per illustrare i concetti ODBC, l'efficienza è talvolta stato riservato a fini di chiarezza. Inoltre, intere sezioni del codice in alcuni casi sono stati omessi per maggiore chiarezza. Tra le definizioni di funzioni non ODBC (tali funzioni i cui nomi non iniziano con "SQL") e la maggior parte di gestione degli errori.  
  
 Tutti gli esempi di codice utilizzano le stringhe ANSI e lo stesso schema di database, viene visualizzato all'inizio di [funzioni di catalogo](../../odbc/reference/develop-app/catalog-functions.md).  
  
## <a name="recommended-reading"></a>Argomenti consigliati  
 Per ulteriori informazioni su SQL, sono disponibili ai seguenti standard:  
  
-   Linguaggio di database, ovvero SQL con integrità miglioramento, ANSI, ANSI 1989 X3.135-1989.  
  
-   Linguaggio di database, SQL: X3H2 ANSI e ISO/IEC 9075:1992 SC21/JTC1/WG3 (SQL-92).  
  
-   Apri gruppo, gestione dei dati: Structured Query Language (SQL), versione 2 (The Open Group, 1996).  
  
 Oltre a standard e le guide SQL specifico del fornitore, molti libri descrivono SQL, tra cui:  
  
-   Date, J. c, con Darwen, Hugh: *una Guida per lo Standard SQL* (Addison-Wesley, 1993).  
  
-   Emerson, L. Sandra, Darnovsky, Maria e Bowman, s Judith: *le pratiche SQL per l'uso* (Addison-Wesley, 1989).  
  
-   Groff, James r e Weinberg, N. di Paul: *utilizzando SQL* (Osborne McGraw-Valeria 1990).  
  
-   Gruber, Martin: *comprensione SQL* (Sybex, 1990).  
  
-   Hursch, L. presa e J. Carolyn: *SQL, Structured Query Language* (scheda documentazione, 1988).  
  
-   Melton, Gianni e Simon, R. Alan: *comprendere il nuovo codice SQL: una guida completa* (Morgan Kaufmann Publishers, 1993).  
  
-   La convenzione Pascal, Fabian: *SQL e nozioni di base relazionale* (M & T documentazione, 1990).  
  
-   Trimble, J. Harvey, Jr e Chappell, David: *un'introduzione a SQL Visual* (Wiley, 1989).  
  
-   Der furgone LAN, Rick F.: *Introduzione a SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren: *SQL e database relazionali* (Microtrend documentazione, 1990).  
  
-   Viescas, John: *Guida di riferimento rapido per SQL* (Microsoft Corp., 1989).  
  
 Per ulteriori informazioni sull'elaborazione delle transazioni, vedere:  
  
-   Grigio, N. J. e Reuter, Andreas: *l'elaborazione delle transazioni: concetti e tecniche* (Morgan Kaufmann Publishers, 1993).  
  
-   Hackathorn, D. Richard: *connettività al Database Enterprise* (Wiley & figli, 1993).  
  
 Per ulteriori informazioni sulle interfacce a livello di chiamata, sono disponibili ai seguenti standard:  
  
-   Open Group, *gestione dati: SQL livello interfaccia Call (CLI), C451* (Open Group, 1995).  
  
-   ISO/IEC 9075-3:1995, interfaccia a livello di chiamata (SQL/CLI).  
  
 Per ulteriori informazioni su ODBC, un numero di valori possibili è disponibile, tra cui:  
  
-   Geiger, Kyle: *all'interno di ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, Charpentier, Luc, Oelschlager, Jon, ortopedico, Andrew, croce, Jim e Lilley, W. Albert: *tramite ODBC 2* (Que, 1994).  
  
-   Johnston, Tom e Osborne, contrassegnare: *ODBC Developers Guide* (Howard W. Sams & società, 1994).  
  
-   Europa settentrionale, Davide: *programmazione Multi-DBMS Windows: utilizzando C++, Visual Basic, ODBC, OLE 2 e strumenti per i progetti DBMS* (John Wiley & figli, Inc., 1995).  
  
-   Stegman, O. Michael, Signore, Robert e Creamer, John: *la soluzione ODBC, Open Database Connectivity in ambienti distribuiti* (McGraw Ruspini, 1995).  
  
-   Welch, Keith: *tramite ODBC 2* (Que, 1994).  
  
-   Merlano, fattura: *Impara gli ODBC 21 giorni* (Howard W. Sams & società, 1994).
