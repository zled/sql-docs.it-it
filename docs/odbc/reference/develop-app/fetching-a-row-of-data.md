---
title: Recupero di una riga di dati | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQLFetch function [ODBC], fetching a row of data
- cursors [ODBC], fetching rows
- result sets [ODBC], fetching
- fetches [ODBC], row of data
ms.assetid: 16d4a380-0d83-456b-aeee-f10738944e86
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 81fff470f916155e9b6d85571db46c46d9e63454
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="fetching-a-row-of-data"></a>Recupero di una riga di dati
Per recuperare una riga di dati, un'applicazione chiama **SQLFetch**. **SQLFetch** può essere chiamato con qualsiasi tipo di cursore, ma solo sposta il cursore del set di righe in una direzione forward-only. **SQLFetch** sposta il cursore alla riga successiva e restituisce i dati per tutte le colonne che sono stati associati con chiamate a **SQLBindCol**. Quando il cursore raggiunge la fine del risultato è stato impostato, **SQLFetch** restituisce SQL_NO_DATA. Per esempi di chiamata **SQLFetch**, vedere [SQLBindCol utilizzando](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Esattamente come **SQLFetch** viene implementato è specifico del driver, ma generale modello è per il driver recuperare i dati per le colonne associate dell'origine dati, convertirlo in base ai tipi di variabili associate e inserire la convertire i dati di tali variabili. Se il driver non è possibile convertire i dati, **SQLFetch** restituisce un errore. L'applicazione possa continuare il recupero delle righe, ma i dati per la riga corrente vanno persi. Cosa accade ai dati delle colonne non associate dipende dal driver, ma la maggior parte dei driver di recuperare e annullare le modifiche o mai recuperare.  
  
 Il driver imposta anche i valori di un buffer di lunghezza/indicatore che sono stati associati. Se il valore di dati per una colonna è NULL, il driver imposta il buffer di lunghezza/indicatore corrispondente su SQL_NULL_DATA. Se il valore di dati non è NULL, il driver imposta il buffer di lunghezza/indicatore per la lunghezza in byte dei dati dopo la conversione. Se non è possibile determinare la lunghezza, come accade a volte con dati di tipo long che viene recuperati da più di una chiamata di funzione, il driver imposta il buffer di lunghezza/indicatore per SQL_NO_TOTAL. Per i tipi di dati a lunghezza fissa, ad esempio numeri interi e strutture di data, la lunghezza in byte è la dimensione del tipo di dati.  
  
 Per i dati a lunghezza variabile, ad esempio carattere e dati binari, il driver verificherà la lunghezza in byte dei dati convertiti contro la lunghezza in byte del buffer associato alla colonna; lunghezza del buffer è incluso il *BufferLength* argomento in **SQLBindCol**. Se la lunghezza in byte dei dati convertiti è maggiore della lunghezza di byte del buffer, il driver tronca i dati per il buffer, restituisce la lunghezza non troncata nel buffer di lunghezza/indicatore, restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01004 (dati inseriti troncato) dalla diagnostica. L'unica eccezione è se un segnalibro a lunghezza variabile viene troncato quando restituito da **SQLFetch**, che restituisce SQLSTATE 22001 (dati String, troncati a destra).  
  
 Dati a lunghezza fissa non viene mai troncati, perché il driver presuppone che la dimensione del buffer associati sia la dimensione del tipo di dati. Il troncamento dei dati tende a essere rari, poiché l'applicazione viene in genere associato un buffer sufficientemente grande da contenere l'intero valore dei dati; Determina le dimensioni necessarie dai metadati. Tuttavia, l'applicazione potrebbe associare in modo esplicito un buffer informarlo che può per essere troppo piccole. Potrebbe ad esempio, recuperare e visualizzare i primi 20 caratteri della descrizione di una parte o i primi 100 caratteri di una colonna di testo lungo.  
  
 Dati di tipo carattere devono essere con terminazione null dal driver prima che venga restituito all'applicazione, anche se è stato troncato. Il carattere di terminazione null non è inclusa la lunghezza di byte restituita ma richiede spazio nel buffer del binding. Si supponga, ad esempio, un'applicazione utilizza stringhe composte da dati di tipo carattere nel set di caratteri ASCII, un driver è 50 caratteri dei dati da restituire e buffer dell'applicazione è 25 byte. Nel buffer dell'applicazione, il driver restituisce i primi 24 caratteri seguiti da un carattere di terminazione null. Nel buffer di lunghezza/indicatore, viene restituito una lunghezza in byte pari a 50.  
  
 L'applicazione è possibile limitare il numero di righe nel set di risultati tramite l'impostazione dell'attributo di istruzione SQL_ATTR_MAX_ROWS prima di impostare l'esecuzione dell'istruzione che crea il risultato. La modalità di anteprima in un'applicazione utilizzata per formattare i report, ad esempio, è necessario solo il numero di dati sufficienti per visualizzare la prima pagina del report. Limitando le dimensioni del set di risultati, tale funzionalità viene eseguita più velocemente. Questo attributo dell'istruzione è progettato per ridurre il traffico di rete e potrebbe non essere supportato da tutti i driver.
