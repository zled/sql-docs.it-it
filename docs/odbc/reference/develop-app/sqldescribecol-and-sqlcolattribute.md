---
title: SQLDescribeCol e SQLColAttribute | Documenti Microsoft
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
- SQLColAttribute function [ODBC], and SQLDescribeCol
- SQLDescribeCol function [ODBC], and SQLColAttribute
- result sets [ODBC], metadata
- retrieving result set meta data [ODBC]
- metadata [ODBC], result set
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a80ccf6ed695433a109770a567f50d100fd3a33
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol e SQLColAttribute
**SQLDescribeCol** e **SQLColAttribute** vengono utilizzati per recuperare i metadati dei set di risultati. La differenza tra queste due funzioni è che **SQLDescribeCol** restituisce sempre la stesse e cinque le informazioni (una colonna nome, tipo di dati, precisione, scala e supporto di valori null), mentre **SQLColAttribute** restituisce una singola informazione richiesto dall'applicazione. Tuttavia, **SQLColAttribute** può restituire una selezione molto più ricche di metadati, tra cui distinzione maiuscole/minuscole di una colonna, visualizzare la dimensione, aggiornamento e la ricerca.  
  
 Molte applicazioni, specialmente quelle che visualizzano solo i dati, richiedono solo i metadati restituiti da **SQLDescribeCol**. Per queste applicazioni, risulta più veloce usare **SQLDescribeCol** di **SQLColAttribute** perché le informazioni vengono restituite in una singola chiamata. Altre applicazioni, specialmente quelle che di aggiornare i dati richiedono metadati aggiuntivi restituiti **SQLColAttribute** e pertanto utilizzare entrambe le funzioni. Inoltre, **SQLColAttribute** supporta i metadati specifici del driver; per ulteriori informazioni, vedere [tipi di dati specifici del Driver, descrittore di tipi, tipi di informazioni, tipi di diagnostica e gli attributi](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Un'applicazione può recuperare i metadati dei set di risultati in qualsiasi momento dopo un'istruzione è stata preparata o eseguita e prima del cursore sul risultato del set è chiuso. Poche applicazioni richiedono metadati del set di risultati dopo l'istruzione viene preparata e prima che venga eseguito. Se possibile, le applicazioni devono attendere per recuperare i metadati fino a dopo l'istruzione viene eseguita, poiché alcune origini dati non possono restituire i metadati per le istruzioni preparate e questa funzionalità nel driver di emulazione è spesso un processo lento. Ad esempio, il driver potrebbe generare un risultato zero righe impostato tramite la sostituzione il **in cui** clausola di un **selezionare** istruzione con la clausola **WHERE 1 = 2** e l'esecuzione di istruzione risultante.  
  
 I metadati sono spesso costosi da recuperare dall'origine dati. Per questo motivo, i driver devono memorizzare nella cache i metadati sono recuperare dal server e tenere premuto che per fino a quando il cursore sul risultato del set è aperto. Inoltre, le applicazioni devono richiedere solo i metadati che sono assolutamente necessario.

