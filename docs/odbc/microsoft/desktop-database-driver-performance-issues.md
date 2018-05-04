---
title: Problemi di prestazioni del Driver di Database desktop | Documenti Microsoft
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
- ODBC desktop database drivers [ODBC], performance
- desktop database drivers [ODBC], performance
- Jet-based ODBC drivers [ODBC], performance
ms.assetid: 1a4c4b7e-9744-411f-9b6e-06dfdad92cf7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73261681421546dcec4cd37d73b1cdf55968038e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="desktop-database-driver-performance-issues"></a>Problemi di prestazioni di Database Desktop Driver
Per garantire la compatibilità con le applicazioni esistenti ANSI, i tipi di dati SQL_WCHAR, SQL_WVARCHAR e SQL_WLONGVARCHAR vengono esposti come SQL_CHAR e SQL_VARCHAR SQL_LONGVARCHAR per Microsoft Access 4.0 o superiore alle origini dati. Le origini dati non restituiscono i tipi di dati carattere "wide", ma i dati devono essere ancora inviati agli Jet in formato carattere Wide. È importante comprendere che la conversione avrà luogo se una colonna di parametro o un risultato SQL_C_CHAR è associata a un tipo di dati SQL_CHAR in un'applicazione ANSI.  
  
 Questa conversione può essere particolarmente efficiente in termini di memoria quando un tipo SQL_C_CHAR è associato a un parametro di tipo LONGVARCHAR. Poiché il motore Jet 4.0 è in grado di flusso di dati del parametro LONGTEXT, deve essere allocato un buffer di conversione UNICODE che è due volte la dimensione del buffer SQL_C_CHAR ANSI. Il meccanismo più efficace è per l'applicazione eseguire la conversione di UNICODE e associare il parametro come tipo SQL_C_WCHAR. Quando un parametro è contrassegnato come data-at-execution e i dati vengono forniti in più chiamate a SQLPutData, un buffer di dati longtext viene aumentato. Un modo per evitare il costo di aumento delle dimensioni di questo buffer "Inserire dati" è fornire una lunghezza facoltativa tramite SQL_DATA_AT_EXEC_LEN(x), in cui *x* è la lunghezza prevista di byte. Le dimensioni di un buffer interno PutData per verrà inizializzato *x* byte.  
  
> [!NOTE]  
>  Un modo efficiente per inserire o aggiornare i dati di tipo long può essere eseguito tramite **SQLBulkOperations()** o **SQLSetPos()** e l'impostazione di dati long a SQL_DATA_AT_EXEC. (EXEC_LEN viene ignorato in questo caso). Dati possono essere trasmessi in blocchi chiamando **SQLPutData** più volte, che in modo efficace i dati verranno aggiunti alla tabella.  
  
 Quando un'applicazione che utilizza un database Jet 3.5 tramite i driver Microsoft ODBC Desktop Database viene aggiornata alla versione 4.0, potrebbe verificarsi un peggioramento delle prestazioni e un'aumento dimensione del working set. Infatti, quando una versione 3. *x* database viene aperta utilizzando la nuova versione 4.0 del driver, il caricamento di Jet 4.0. Quando viene aperto il database Jet 4.0 e si vede che il database è 3. *x* versione, viene caricato un driver ISAM installabile che equivale a caricare anche il motore Jet 3.5. Per rimuovere la riduzione delle prestazioni e le dimensioni, Jet 3. *x* database debba essere compressi in un database nel formato di Jet 4.0. Verrà eliminare il caricamento di due motori di Jet e ridurre al minimo il percorso del codice ai dati.  
  
 Inoltre, il motore Jet 4.0 è un motore di Unicode. Tutte le stringhe vengono memorizzate e modificate in formato Unicode. Quando un'applicazione ANSI accede a un Jet 3. *x* database attraverso il motore Jet 4.0, i dati viene convertito da ANSI a Unicode e torna ad ANSI. Se il database viene aggiornato per il formato della versione 4.0, le stringhe vengono convertite in Unicode, la rimozione di un livello di conversione di stringhe, nonché di ridurre al minimo il percorso del codice ai dati attraverso un solo motore Jet.
