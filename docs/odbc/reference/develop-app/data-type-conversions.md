---
title: Conversioni di tipi di dati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], conversions
- SQL data types [ODBC], conversions
- converting data [ODBC]
- converting data types [ODBC]
- C data types [ODBC], conversions
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2369b39ff415a5387205ce62811594fe08a9f324
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-conversions"></a>Conversioni di tipi di dati
Dati possono essere convertiti da un tipo a altro in uno dei quattro volte: quando dati viene trasferiti dalla variabile di un'applicazione a un altro (C per C), all'invio dei dati in una variabile di applicazione a un parametro di istruzione C a SQL, quando i dati in una colonna del set di risultati viene restituiti una variabile di applicazione (SQL per C) e quando i dati vengono trasferiti dall'origine dati di una colonna a un altro (SQL to SQL).  
  
 Qualsiasi conversione che si verifica quando i dati vengono trasferiti dalla variabile di un'applicazione a un altro è all'esterno dell'ambito di questo documento.  
  
 Quando un'applicazione associa una variabile a un parametro di colonna o l'istruzione set di risultati, l'applicazione specifica in modo implicito una conversione del tipo di dati per la scelta del tipo di dati della variabile di applicazione. Si supponga, ad esempio, che una colonna contiene dati di tipo integer. Se l'applicazione associa una variabile integer per la colonna, specifica che non venga eseguita alcuna conversione; Se l'applicazione associa una variabile di caratteri per la colonna, specifica che i dati di essere convertita da integer in carattere.  
  
 ODBC definisce la modalità di conversione dei dati tra i diversi tipi di dati SQL e C. In pratica, ODBC supporta tutte le conversioni ragionevole, ad esempio carattere da integer e integer in float e non supporta le conversioni in modo non corretto, ad esempio float alla data. I driver devono supportare tutte le conversioni per ogni tipo di dati SQL che supportano. Per un elenco completo delle conversioni tra tipi di dati SQL e C, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) e [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) appendice d: tipo di dati.  
  
 ODBC definisce anche una funzione scalare per la conversione dei dati da un tipo di dati SQL a un altro. Il **CONVERTIRE** viene eseguito il mapping di funzione scalare dal driver per la funzione scalare sottostante o funzioni definite per eseguire conversioni nell'origine dati. Poiché viene eseguito il mapping di questa funzione per funzioni specifiche del sistema DBMS, ODBC non definisce il funzionamento di queste conversioni o quali conversioni devono essere supportate. Un'applicazione consente di individuare quali conversioni sono supportate da un particolare driver e l'origine dati tramite le opzioni SQL_CONVERT **SQLGetInfo**. Per ulteriori informazioni sul **CONVERTIRE** funzione scalare, vedere [sequenze di Escape ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) e [esplicita funzione di conversione di tipi di dati](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).

