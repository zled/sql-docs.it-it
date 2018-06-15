---
title: Gestione Driver | Documenti Microsoft
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
- driver manager [ODBC]
- ODBC architecture [ODBC], driver manager
- driver manager [ODBC], about driver manager
- ODBC driver manager [ODBC]
ms.assetid: 559e4de1-16c9-4998-94f5-6431122040cd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d31dbfce3f5c5e3b09f43ec9a644e415b6d82d22
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918526"
---
# <a name="the-driver-manager"></a>Gestione Driver
Il *gestione Driver* è una libreria che gestisce la comunicazione tra applicazioni e driver. Ad esempio, nelle piattaforme Microsoft® Windows®, gestione Driver è una libreria a collegamento dinamico (DLL) che viene scritto da Microsoft e può essere ridistribuita dagli utenti del SDK di ridistribuibile MDAC 2.8 SP1.  
  
 Gestione Driver esiste principalmente per motivi di praticità per i writer di applicazione e un numero di problemi comuni a tutte le applicazioni è stato risolto. Tra cui determinare quale driver caricare basata su un nome di origine dati, durante il caricamento e scaricamento di driver e chiamata di funzioni nei driver.  
  
 Per capire perché quest'ultimo sia un problema, si consideri cosa accadrebbe se l'applicazione ha chiamato funzioni nel driver direttamente. A meno che l'applicazione è stata collegata direttamente a un driver specifico, sarebbe necessario compilare una tabella di puntatori a funzioni nel driver e chiamare tali funzioni dal puntatore. Utilizzando lo stesso codice per più di un driver in un momento aggiungere un ulteriore livello di complessità. L'applicazione sarebbe necessario innanzitutto impostare un puntatore a funzione in modo da puntare alla funzione corretta nel driver corretti e quindi chiamare la funzione tramite tale puntatore.  
  
 Gestione Driver risolve questo problema, fornendo un'unica posizione per chiamare ogni funzione. L'applicazione viene collegata alle funzioni ODBC Driver Manager e le chiamate in Gestione Driver, non il driver. L'applicazione identifica l'origine di driver e i dati di destinazione con un *handle di connessione*. Quando viene caricato un driver, Driver Manager crea una tabella di puntatori a funzioni nel driver. Si utilizza l'handle di connessione passato dall'applicazione per trovare l'indirizzo della funzione del driver di destinazione e chiama tale funzione in base all'indirizzo.  
  
 La maggior parte, gestione Driver passa solo le chiamate di funzione dall'applicazione per il driver corretto. Tuttavia, implementa inoltre alcune funzioni (**SQLDataSources**, **SQLDrivers**, e **SQLGetFunctions**) ed esegue il controllo degli errori di base. Gestione Driver, ad esempio, verifica che gli handle non sono puntatori null, che le funzioni vengono chiamate nell'ordine corretto e che alcuni argomenti di funzione sono validi. Per una descrizione completa degli errori controllata da Gestione Driver, vedere la sezione di riferimento per ogni funzione e [tabelle di transizione dello stato di appendice b: ODBC](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Il ruolo principale finale di gestione Driver è caricamento e scaricamento di driver. L'applicazione carica e Scarica solo i Driver Manager. Quando desidera utilizzare un driver specifico, chiama una funzione di connessione (**SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**) in Gestione Driver e specifica il nome di una determinata origine dati o i driver, ad esempio "Contabilità" o "SQL Server". Utilizza questo nome, gestione Driver consente di cercare le informazioni di origine dati per nome file del driver, ad esempio Sqlsrvr.dll. Quindi caricato il driver (presupponendo che non sia già caricato) archivia l'indirizzo di ogni funzione nel driver e chiama la funzione di connessione nel driver, che quindi inizializzato e si connette all'origine dati.  
  
 Quando viene eseguita l'applicazione usa il driver, chiama **SQLDisconnect** the Driver Manager. Gestione Driver chiama questa funzione nel driver si disconnette dall'origine dati. Tuttavia, gestione Driver mantiene il driver in memoria nel caso in cui l'applicazione si riconnette a esso. Scarica il driver solo quando l'applicazione libera la connessione utilizzata dal driver o utilizza la connessione di un altro driver e le altre connessioni non utilizzano il driver. Per una descrizione completa del ruolo di gestione Driver nel caricamento e scaricamento di driver, vedere [di gestione Driver ruolo nel processo di connessione](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).
