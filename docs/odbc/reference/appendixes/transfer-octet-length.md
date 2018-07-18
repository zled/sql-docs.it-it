---
title: Trasferire la lunghezza dell'ottetto | Documenti Microsoft
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
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- data types [ODBC], transfer octet length
ms.assetid: 9fdc9762-e203-4cff-9212-54f450bf18d9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 157dbea8954dd7823888360c7d9cf74d9c8db74d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909758"
---
# <a name="transfer-octet-length"></a>Lunghezza dell'ottetto trasferimento
La lunghezza di ottetti di trasferimento di una colonna è il numero massimo di byte restituiti all'applicazione quando i dati vengono trasferiti al relativo tipo di dati C predefinito. Dati di tipo carattere, la lunghezza di ottetti di trasferimento non include lo spazio per il carattere di terminazione null. La lunghezza di ottetti di trasferimento di una colonna può essere diversa dal numero di byte necessari per archiviare i dati nell'origine dati.  
  
 La lunghezza di ottetti trasferimento definita per ogni tipo di dati SQL ODBC è illustrata nella tabella seguente.  
  
|Identificatore di tipo SQL|Lunghezza|  
|-------------------------|------------|  
|Tutti i tipi di carattere [a]|Definita o la lunghezza massima (per tipo di variabile) della colonna in byte. Questo è lo stesso valore del campo del descrittore SQL_DESC_OCTET_LENGTH.|  
|SQL_DECIMAL<br />SQL_NUMERIC|Il numero di byte necessari per contenere la rappresentazione dei caratteri dei dati se il set di caratteri ANSI e due volte questo numero, se il set di caratteri UNICODE. Questo è il numero massimo di cifre più di due, perché i dati vengono restituiti come stringa di caratteri e di caratteri necessari per le cifre e un segno di un separatore decimale. Ad esempio, la lunghezza di trasferimento di una colonna definita come NUMERIC(10,3) è 12.|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT|Il numero di byte necessari per contenere la rappresentazione dei caratteri dei dati se il set di caratteri ANSI e due volte questo numero, se il set di caratteri UNICODE, perché questo tipo di dati viene restituito come una stringa di caratteri per impostazione predefinita. La rappresentazione di caratteri è costituito da 20 caratteri: 19 cifre e il segno, se firmato o 20 cifre, se unsigned. Pertanto, la lunghezza è pari a 20.|  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|Tutti i tipi binari [a]|Il numero di byte necessari per contenere definito (per i tipi) o numero massimo (per i tipi di variabile) di caratteri.|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (la dimensione della struttura di valore SQL_DATE_STRUCT o SQL_TIME_STRUCT).|  
|SQL_TYPE_TIMESTAMP|16 (la dimensione della struttura di SQL_TIMESTAMP_STRUCT).|  
|Tutti i tipi di dati di intervallo|34 (la dimensione della struttura di intervallo).|  
|SQL_GUID|16 (la dimensione della struttura di GUID).|  
  
 [a] se il driver non è possibile determinare la lunghezza della colonna o parametro per i tipi di variabile, restituirà SQL_NO_TOTAL.
