---
title: Limitazioni del tipo di dati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac29132cf37fe6e4b13774826dd2467243e152fe
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="data-type-limitations"></a>Limitazioni del tipo di dati
I driver di Database di Microsoft ODBC Desktop imporre le limitazioni sui tipi di dati seguenti:  
  
|Tipo di dati|Description|  
|---------------|-----------------|  
|Tutti i tipi di dati|Errori di conversione di tipo potrebbero comportare la colonna interessata viene impostata su NULL.|  
|BINARY|Creazione di una colonna BINARY di lunghezza zero restituisce una colonna BINARY 255 byte.|  
|DATE|Il tipo di dati di data non può essere convertito in un altro tipo di dati (o stesso) dalla funzione CONVERT.|  
|DECIMAL (numerico esatto)|Non supportato.|  
|Tipi di dati a virgola mobile|Il numero di posizioni decimali nel numero a virgola mobile può essere limitato dal formato del numero impostato nella sezione internazionale del Pannello di controllo di Windows.|  
|NUMERIC|Supporta la precisione massima e una scala di 28.|  
|timestamp|Impossibile convertire il tipo di dati TIMESTAMP a se stesso per la funzione CONVERT.|  
|TINYINT|I valori di tipo TINYINT sono sempre senza segno.|  
|Stringhe di lunghezza zero|Quando viene utilizzato un file dBASE, Microsoft Excel, Paradox o Textdriver, inserire una stringa di lunghezza zero in una colonna effettivamente inserisce un valore NULL invece.|
