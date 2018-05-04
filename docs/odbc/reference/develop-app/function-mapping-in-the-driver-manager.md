---
title: Funzione di Mapping in Gestione Driver | Documenti Microsoft
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
- Unicode [ODBC], functions
- driver manager [ODBC], function mapping
- functions [ODBC], Unicode functions
ms.assetid: ff093b29-671a-4fc0-86c9-08a311a98e54
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 710a3edd3afcc3d82e18875de330d15b048a5b3f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="function-mapping-in-the-driver-manager"></a>Mapping di funzione in Gestione Driver
Gestione driver supporta due punti di ingresso per le funzioni che accettano argomenti di stringa. La funzione non decorata (**SQLDriverConnect**) è il formato ANSI della funzione. Il formato Unicode è decorato con un *W* (**SQLDriverConnectW**.)  
  
 Il file di intestazione ODBC supporta inoltre funzioni decorate con un *A,* (**SQLDriverConnectA**) per la praticità di applicazioni ANSI o Unicode miste. Le chiamate effettuate per il **A** funzioni sono in realtà chiama il punto di ingresso non decorato (**SQLDriverConnect**.)  
  
 Se l'applicazione viene compilata con Unicode **#define**, il file di intestazione ODBC verrà eseguito il mapping di chiamate di funzione non decorato (**SQLDriverConnect**) per la versione Unicode (**SQLDriverConnectW** .)  
  
 Gestione Driver riconosce un driver come driver Unicode se **SQLConnectW** è supportato dal driver.  
  
 Se il driver è un driver di Unicode, gestione Driver effettua chiamate di funzione come segue:  
  
-   Passa direttamente tramite una funzione senza parametri o gli argomenti di stringa per il driver.  
  
-   Passa le funzioni Unicode (con il *W* suffisso) direttamente tramite il driver.  
  
-   Converte una funzione ANSI (con il *A* suffisso) a una funzione Unicode (con il *W* suffisso) per convertire gli argomenti di stringa in Unicode i caratteri e la funzione Unicode viene passata al driver.  
  
 Se il driver è un driver ANSI, gestione Driver effettua chiamate di funzione come segue:  
  
-   Passa funzioni senza argomenti di stringa o i parametri direttamente tramite il driver.  
  
-   Converte le funzioni Unicode (con il *W* suffisso) in un formato ANSI chiamata di funzione e lo passa al driver.  
  
-   Passa una funzione ANSI direttamente al driver.  
  
 Gestione Driver è abilitata per Unicode internamente. Di conseguenza, le prestazioni ottimali viene ottenuta da un'applicazione Unicode utilizzano un driver di Unicode, in quanto Gestione Driver passa semplicemente funzioni Unicode tramite il driver. Quando un'applicazione ANSI collabora con un driver ANSI, gestione Driver deve convertire le stringhe da ANSI a Unicode durante l'elaborazione di alcune funzioni, ad esempio **SQLDriverConnect**. Dopo la funzione di elaborazione, gestione Driver deve convertire quindi la stringa Unicode al ANSI prima di inviare la funzione al driver ANSI.  
  
 Un'applicazione non deve modificare o leggere il buffer dei parametri associati, quando il driver restituisce SQL_NEED_DATA o SQL_STILL_EXECUTING. Gestione Driver lascia il buffer associato a ANSI fino a quando il driver restituisce SQL_SUCCESS, SQL_SUCCESS_WITH_INFO o SQL_ERROR. Un'applicazione multithreading non deve ottenere l'accesso a tutti i valori di parametri associati in un altro thread in esecuzione un'istruzione SQL. Gestione Driver converte i dati da Unicode ad ANSI "sul posto" e l'altro thread potrebbe visualizzare dati di ANSI in questi buffer mentre il driver è in corso l'elaborazione dell'istruzione SQL. Applicazioni che associano i dati Unicode a un driver ANSI non necessario associare due colonne diverse per lo stesso indirizzo.
