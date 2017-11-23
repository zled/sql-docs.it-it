---
title: Lunghezza dei dati, lunghezza del Buffer e il troncamento | Documenti Microsoft
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
helpviewer_keywords:
- data buffers [ODBC], length
- data length [ODBC]
- truncating data [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 2825c6e7-b9ff-42fe-84fc-7fb39728ac5d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 978418b3341bf82e0d7560052e68fecbbeb3c59b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="data-length-buffer-length-and-truncation"></a>Lunghezza dei dati, lunghezza del Buffer e il troncamento
Il *lunghezza dei dati* è la lunghezza in byte dei dati potrebbe essere memorizzato nel buffer di dati dell'applicazione, non viene archiviato nell'origine dati. Questa distinzione è importante perché i dati vengono spesso archiviati in tipi diversi nel buffer di dati nell'origine dati. Pertanto, per i dati inviati all'origine dati, questa è la lunghezza in byte dei dati prima della conversione al tipo dell'origine dati. Per i dati recuperati dall'origine dati, questa è la lunghezza in byte dei dati dopo la conversione al tipo di buffer di dati e prima che venga eseguita qualsiasi troncamento.  
  
 Per i dati a lunghezza fissa, ad esempio un numero intero o una struttura di data, la lunghezza in byte dei dati è sempre la dimensione del tipo di dati. In generale, le applicazioni di allocare un buffer di dati che è la dimensione del tipo di dati. Se l'applicazione alloca un buffer più piccolo, le conseguenze sono definite in quanto il driver presuppone che il buffer dei dati è la dimensione del tipo di dati e troncare i dati per un buffer più piccoli. Se l'applicazione consente di allocare un buffer più grande, lo spazio aggiuntivo non viene mai utilizzato.  
  
 Per i dati a lunghezza variabile, ad esempio carattere o dati binari, è importante tenere presente che la lunghezza in byte dei dati è distinto e spesso diverso la lunghezza in byte del buffer. La relazione di questi due lunghezze è descritta nel [buffer](../../../odbc/reference/develop-app/buffers.md) sezione. Se la lunghezza in byte dei dati è maggiore della lunghezza di byte del buffer, il driver tronca i dati recuperati per la lunghezza in byte del buffer e restituisce SQL_SUCCESS_WITH_INFO con SQLSTATE 01004 (dati troncati). Tuttavia, la lunghezza di byte restituita è la lunghezza dei dati non troncati.  
  
 Si supponga, ad esempio, che un'applicazione alloca 50 byte per un buffer di dati binari. Se il driver ha 10 byte di dati binari da restituire, restituisce i 10 byte nel buffer. La lunghezza in byte dei dati è 10 e la lunghezza in byte del buffer è 50. Se il driver ha 60 byte di dati binari da restituire, tronca i dati di 50 byte, restituisce i byte nel buffer e restituisce SQL_SUCCESS_WITH_INFO. La lunghezza in byte dei dati è 60 (lunghezza prima troncamento) e la lunghezza in byte del buffer è ancora 50.  
  
 Viene creato un record di diagnostica per ogni colonna che viene troncato. Poiché il tempo per il driver a creare questi record e per l'applicazione per l'elaborazione, il troncamento può influire negativamente sulle prestazioni. In genere, un'applicazione può evitare questo problema tramite l'allocazione di buffer di grandi dimensioni sufficientemente, anche se ciò potrebbe non essere possibile quando si lavora con dati di tipo long. Quando si verifica un troncamento dei dati, l'applicazione può talvolta allocare un buffer più grande e ripetere il recupero dei dati. Ciò non avviene in tutti i casi. Se si verifica un troncamento durante il recupero dei dati con chiamate a **SQLGetData**, l'applicazione non è necessario chiamare **SQLGetData** per i dati che sono già stata resa; per ulteriori informazioni, vedere [Guida Dati di tipo long](../../../odbc/reference/develop-app/getting-long-data.md).
