---
title: Eseguire l'override di iniziali e la precisione in secondi per i tipi di dati di intervallo | Documenti Microsoft
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
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d00f69e21f00a2e4140af6a81d747471d50c48b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Override iniziale predefinita e la precisione in secondi per i tipi di dati di intervallo
Quando il campo SQL_DESC_TYPE di un ARD è un tipo C di datetime o intervallo, con una chiamata a **SQLBindCol** o **SQLSetDescField**, il campo SQL_DESC_PRECISION (che contiene l'intervallo (secondi) precisione) è impostata per i valori predefiniti seguenti:  
  
-   6 per timestamp e tutti i tipi di dati di intervallo con un secondo componente.  
  
-   0 per tutti gli altri tipi di dati.  
  
 Per tutti i tipi di dati di intervallo, il campo di descrizione SQL_DESC_DATETIME_INTERVAL_PRECISION, che contiene la precisione di campo intervallo iniziale, è impostato su un valore predefinito di 2.  
  
 Quando il campo SQL_DESC_TYPE in un APD è un tipo C di datetime o intervallo, con una chiamata a **SQLBindParameter** o **SQLSetDescField**, di SQL_DESC_PRECISION e SQL_DESC_DATETIME_INTERVAL_ PRECISIONE in APD sono impostati sul valore predefinito specificato in precedenza. Questo vale per i parametri di input ma non per i parametri di input/output o di output.  
  
 Una chiamata a **SQLSetDescRec** imposta l'intervallo di precisione iniziale per l'impostazione predefinita, ma imposta la precisione dei secondi di intervallo (nel campo SQL_DESC_PRECISION) al valore della relativa *precisione* argomento.  
  
 Se uno dei valori predefiniti specificati in precedenza non è accettabile per un'applicazione, l'applicazione deve impostare il campo SQL_DESC_PRECISION o SQL_DESC_DATETIME_INTERVAL_PRECISION chiamando **SQLSetDescField**.  
  
 Se l'applicazione chiama **SQLGetData** per restituire i dati in un valore datetime o intervallo di tipo C, vengono utilizzate la precisione di iniziale intervallo predefinito e la precisione dei secondi di intervallo. Se l'impostazione predefinita non è accettabile, l'applicazione deve chiamare **SQLSetDescField** per impostare un campo di descrizione, o **SQLSetDescRec** impostare SQL_DESC_PRECISION. La chiamata a **SQLGetData** deve avere un *TargetType* di SQL_ARD_TYPE per utilizzare i valori nei campi del descrittore.  
  
 Quando **SQLPutData** viene chiamato, l'intervallo iniziale intervallo e precisione secondi precisione vengono letti dai campi di record del descrittore che corrispondono al parametro data-at-execution o colonna, ovvero APD campi per le chiamate per **SQLExecute** o **SQLExecDirect**, o campi ARD per le chiamate a **SQLBulkOperations** o **SQLSetPos**.
