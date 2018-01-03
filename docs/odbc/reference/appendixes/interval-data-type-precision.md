---
title: Precisione del tipo di dati di intervallo | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
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
- precision [ODBC]
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: eb73bd77-2e7e-4498-a266-4d7c990a0d56
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6551f235c62f502d85f680b1925766a9e43e8eb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="interval-data-type-precision"></a>Precisione del tipo di dati intervallo
Precisione per un tipo di dati di intervallo include intervallo iniziali precisione, intervallo precisione e la precisione in secondi.  
  
 Il campo iniziale di un intervallo è un valore numerico con segno. Il numero massimo di cifre per il campo iniziale è determinato da una quantità chiamata *intervallo, precisione iniziale* che fa parte della dichiarazione di tipo di dati. Ad esempio, la dichiarazione: intervallo HOUR(5) al minuto è un intervallo iniziali precisione di 5; il campo ora può accettare valori di –99999 e 99999. L'intervallo di precisione iniziale è contenuto nel campo SQL_DESC_DATETIME_INTERVAL_PRECISION del record del descrittore.  
  
 Viene chiamato l'elenco dei campi che è un tipo di dati di intervallo è costituito da *precisione intervallo*. Non è un valore numerico, come il termine "precisione" potrebbe implicare. Ad esempio, la precisione di intervallo del tipo di intervallo DAY TO è secondo elenco giorno, ora, minuto, secondo. Nessun campo di descrizione che contiene questo valore. la precisione di intervallo può sempre essere determinata dal tipo di dati di intervallo.  
  
 Qualsiasi tipo di dati di intervallo con un secondo campo ha un *precisione dei secondi*. Questo è il numero di cifre consentite nella parte frazionaria del valore di secondi. È diverso rispetto agli altri tipi di dati, in cui la precisione indica il numero di cifre prima del separatore decimale. La precisione dei secondi di un tipo di dati di intervallo è il numero di cifre dopo il separatore decimale. Ad esempio, se la precisione dei secondi è impostata su 6, 123456 nel campo frazione il numero verrebbe interpretato come.123456 e il numero 1230 verrebbe interpretati come.001230. Per altri tipi di dati, questo viene considerato scala. Precisione in secondi di intervallo è contenuto nel campo SQL_DESC_PRECISION del descrittore. Se la precisione del componente di secondi frazionari del valore di intervallo SQL è maggiore di ciò che possono essere contenuti nella struttura di intervallo C, driver-definito se il valore dei secondi frazionari nell'intervallo di SQL è arrotondato o troncato durante la conversione c struttura di intervallo.  
  
 Quando il campo SQL_DESC_CONCISE_TYPE è impostato su un tipo di dati di intervallo, il campo SQL_DESC_TYPE è impostato per SQL_INTERVAL e il SQL_DESC_DATETIME_INTERVAL_CODE è impostato per il codice per il tipo di dati di intervallo. Il campo SQL_DESC_DATETIME_INTERVAL_PRECISION viene impostato automaticamente alla precisione iniziale intervallo predefinito di 2 e il campo SQL_DESC_PRECISION viene impostato automaticamente per la precisione dei secondi di intervallo predefinito di 6. Se uno di questi valori non è appropriato, l'applicazione deve impostare in modo esplicito il campo di descrizione tramite una chiamata a **SQLSetDescField**.
