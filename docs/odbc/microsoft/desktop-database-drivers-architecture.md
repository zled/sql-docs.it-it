---
title: Architettura di driver di Database desktop | Documenti Microsoft
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
- Jet-based ODBC drivers [ODBC], architecture
- ODBC desktop database drivers [ODBC], architecture
- desktop database drivers [ODBC], architecture
ms.assetid: 8b4d13f7-ab37-40b4-a9c6-145e7385352f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 975e70038bc78962691ea30f885dd0050e508753
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="desktop-database-drivers-architecture"></a>Architettura di driver di Database desktop
Questi driver sono progettati per l'uso in Microsoft Windows 95 o versioni successive o Windows NT 4.0 e Windows 2000. Sono supportate sole applicazioni a 32 bit in Windows 95 o versione successiva. applicazioni a 16 bit e a 32 bit sono supportate in Windows NT 4.0 e Windows 2000.  
  
> [!NOTE]  
>  Per informazioni sulla versione di ODBC da utilizzare con questi driver, vedere il *riferimento per programmatori ODBC*e note sulla versione correnti e precedenti. Ad eccezione delle aree indicate, questi driver conforme al *riferimento per programmatori ODBC*.  
  
 I driver di Database ODBC Desktop includono driver a 32 bit per Microsoft Access, dBASE, Microsoft Excel, Paradox e testo. N. 16 - bit driver sono inclusi. (Un driver per Microsoft FoxPro è disponibile separatamente).  
  
 L'architettura applicazione/driver in Windows 95 o versioni successive è:  
  
 ![App&#47;architettura dei driver: Windows 95 e versioni successive](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 L'utilizzo di questi driver per applicazioni a 16 bit in Windows 95 non è supportato.  
  
 L'architettura applicazione/driver in Windows NT 4.0 e Windows 2000 è:  
  
 ![App&#47;architettura dei driver: NT 4.0 e Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 I driver di Database Desktop sono i driver a due livelli. In una configurazione a due livelli, il driver non esegue il processo di analisi, convalida, l'ottimizzazione e l'esecuzione della query. In alternativa, Microsoft Jet esegue queste attività. Elabora le chiamate all'API ODBC e funge da un motore SQL. Microsoft Jet è diventata una parte integrante, non separabile driver: viene fornito con i driver e risiede con i driver, anche se altre applicazioni nel computer non utilizzarla.  
  
 I driver di Database Desktop è costituito da sei diversi driver, o, più precisamente, un driver file (Odbcjt32.dll) che ODBC [gestione Driver](../../odbc/reference/the-driver-manager.md) utilizza in sei modi diversi. Il flag DRIVERID nella voce del Registro di sistema per un'origine dati determina quali driver in Odbcjt32.dll Usa gestione Driver. L'applicazione passa questo flag nella stringa di connessione, inclusa in una chiamata a **SQLDriverConnect**. Per impostazione predefinita, il flag è l'ID del driver Microsoft Access.  
  
 Il file del programma di installazione driver cambia il flag DRIVERID in fase di installazione. Tutti i driver tranne il driver Microsoft Access dispone di una DLL di configurazione associata. Quando fa clic su **installazione** nel [Amministrazione origine dati ODBC di Microsoft](../../odbc/admin/odbc-data-source-administrator.md) per un'origine dati, il programma di installazione ODBC DLL (Odbcinst.dll) consente di caricare la DLL di installazione. DLL di installazione consente di esportare la funzione di programma di installazione ODBC **SQLConfigDataSource**. Se viene passato un handle di finestra **SQLConfigDataSource**, questa funzione consente di visualizzare una finestra del programma di installazione e cambia il flag DRIVERID in base al driver selezionato dall'interfaccia utente.  
  
 Quando viene creato un file a livello di codice, viene passato un handle di finestra NULL **SQLConfigDataSource**, e la funzione crea un'origine dati in modo dinamico, il flag DRIVERID in base alla modifica di *lpszDriver*argomento nella chiamata di funzione.  
  
 ODBCJT32.dll implementa funzioni ODBC sopra l'API di Microsoft Jet. Non è tuttavia alcun mapping diretto tra le funzioni di ODBC e Microsoft Jet. Molti fattori, ad esempio i modelli di cursore e i mapping di SQL, evitare una correlazione diretta delle funzioni.  
  
 Il driver ODBC si trova tra la gestione di Microsoft Jet e gestione Driver ODBC. Alcune funzioni ODBC chiamati da un'applicazione sono gestite da Gestione Driver e non è stati passati al driver. Per queste funzioni, Microsoft Jet non vede mai la funzione chiamata perché non dispone di una connessione diretta al Driver Manager.
