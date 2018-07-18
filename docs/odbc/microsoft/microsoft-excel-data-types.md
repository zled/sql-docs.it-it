---
title: Tipi di dati di Microsoft Excel | Documenti Microsoft
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
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c1a2c6159f8d0d112e2cae5e1de687f8af3cf2e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-excel-data-types"></a>Tipi di dati di Microsoft Excel
Nella tabella seguente viene illustrato come tipi di dati di Microsoft Excel driver vengono eseguito il mapping ai tipi di dati SQL ODBC. Il driver per Microsoft Excel assegna questi tipi di dati alle colonne nelle tabelle di Microsoft Excel in base ai dati nella colonna.  
  
|Tipo di dati di Microsoft Excel|Tipo di dati ODBC|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|LOGICA|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** restituisce tipi di dati SQL ODBC. Tutte le conversioni nell'appendice D il *riferimento per programmatori ODBC* sono supportati per i tipi di dati SQL ODBC elencati in precedenza in questo argomento.  
  
 La tabella seguente illustra le limitazioni sui tipi di dati di Microsoft Excel.  
  
|Tipo di dati|Description|  
|---------------|-----------------|  
|Dati crittografati|Il driver per Microsoft Excel non è possibile leggere i dati crittografati.|  
|Stringhe di errore|Il driver per Microsoft Excel non può restituire una stringa di caratteri per i valori di errore di Microsoft Excel (# n/a!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, #NULL e!), ma restituisce invece un valore NULL.|  
|LOGICA|Il valore in una colonna LOGICA viene restituito in un buffer SQL_C_CHAR come 0 o 1.|  
|NUMBER|Se viene creata una colonna integer, è possibile immettere numeri che sono troppo grandi per il tipo di dati integer e dati che contiene i valori interi non possono essere inseriti, con il risultato che la colonna può essere convertita in SQL_DOUBLE.|  
|TEXT|Quando le righe di una colonna contengono più di un tipo di dati di Microsoft Excel, il driver ODBC di Microsoft Excel viene assegnato il tipo di dati SQL_VARCHAR alla colonna. Vi è un'eccezione a questa: se la colonna contiene solo due o tre dei tipi di dati datetime (data, ora e data/ora), il driver ODBC di Microsoft Excel viene assegnato il tipo di dati SQL_TIMESTAMP alla colonna.<br /><br /> Creazione di una colonna di testo pari a zero o di lunghezza non specificata restituisce una colonna di 255 byte.<br /><br /> Un valore letterale di stringa di caratteri può contenere qualsiasi carattere ANSI (decimale 1-255). Utilizzare due virgolette singole consecutive (") per rappresentare una virgoletta singola (').<br /><br /> Inserimento di un valore NULL in una colonna con tipo di dati diverso da SQL_VARCHAR causerà il tipo di dati della colonna da modificare per SQL_VARCHAR.|  
  
 Altre limitazioni sui tipi di dati sono reperibili [limitazioni del tipo di dati](../../odbc/microsoft/data-type-limitations.md).
