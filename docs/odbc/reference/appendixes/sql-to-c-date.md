---
title: 'SQL per c: data | Documenti Microsoft'
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
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4aa60f38cec58c37b017763083e6b38525855fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-to-c-date"></a>SQL per c: data
L'identificatore per il tipo di dati SQL ODBC Data è:  
  
 SQL_TYPE_DATE  
  
 Nella tabella seguente viene illustrato ODBC C a tipi di dati a cui può essere convertito i dati SQL Data. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > lunghezza in byte di caratteri<br /><br /> 11 < = *BufferLength* < = lunghezza in byte di caratteri<br /><br /> *BufferLength* < 11|data<br /><br /> Dati troncati<br /><br /> Non definito|10<br /><br /> Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > lunghezza in caratteri<br /><br /> 11 < = *BufferLength* < = lunghezza in caratteri<br /><br /> *BufferLength* < 11|data<br /><br /> Dati troncati<br /><br /> Non definito|10<br /><br /> Lunghezza dei dati in caratteri<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Nessuno, [a]|data|6 [c]|n/d|  
|SQL_C_TYPE_TIMESTAMP|Nessuno, [a]|Dati [b]|16 [c]|n/d|  
  
 [a] il valore di *BufferLength* viene ignorata per la conversione. Il driver presuppone che le dimensioni di **TargetValuePtr* è la dimensione del tipo di dati C.  
  
 [b] i campi di tempo della struttura di timestamp vengono impostati su zero.  
  
 [c] è la dimensione del tipo di dati C corrispondente.  
  
 Quando i dati SQL Data viene convertito in dati di tipo carattere C, la stringa risultante è il "*aaaa*-*mm*-*gg*" formato. Questo formato non è interessato dalla configurazione dell'impostazione di paese Windows®.
