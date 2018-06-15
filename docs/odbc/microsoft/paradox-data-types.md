---
title: Tipi di dati Paradox | Documenti Microsoft
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
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43c117a9026c1d00b879ab88892cb2b234894646
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903116"
---
# <a name="paradox-data-types"></a>Tipi di dati Paradox
Il driver ODBC Paradox esegue il mapping di tipi di dati Paradox ai tipi di dati SQL ODBC. Nella tabella seguente elenca tutti i tipi di dati Paradox e Mostra ODBC SQL sono mappate per i tipi di dati.  
  
|Tipo di dati Paradox|Tipo di dati ODBC|  
|-----------------------|--------------------|  
|ALFANUMERICO|SQL_VARCHAR|  
|INCREMENTO AUTOMATICO [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|BYTE [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|IMMAGINE DI [2]|SQL_LONGVARBINARY|  
|LOGICA [1]|SQL_BIT|  
|LONG [1]|SQL_INTEGER|  
|MEMO [2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|BREVE|SQL_SMALLINT|  
|TEMPO [1]|SQL_TIMESTAMP|  
|TIMESTAMP [1]|SQL_TIMESTAMP|  
  
 [1] valido solo per le versioni Paradox 5. *x*.  
  
 [2] valido solo per le versioni Paradox 4. *x* e 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** restituisce tipi di dati SQL ODBC. Tutte le conversioni nell'appendice D il *riferimento per programmatori ODBC* sono supportati per i tipi di dati SQL ODBC elencati in precedenza in questo argomento.  
  
 La tabella seguente illustra le limitazioni sui tipi di dati Paradox.  
  
|Tipo di dati|Description|  
|---------------|-----------------|  
|ALFANUMERICO|Creazione di una colonna ALFANUMERICA pari a zero o di lunghezza non specificata restituisce una colonna di 255 byte.|  
|BYTES|Se si inserisce NULL in una colonna binaria con il driver Paradox5, questo viene su 0.|  
|LONG|Il valore negativo massimo supportato dal driver per il tipo di dati Long in Paradox 5 Paradox. *x* non è -2 ^ 31 (-2147483648), dal momento che lungo associato ai dati ODBC devono essere digitare SQL_INTEGER. Il valore negativo massimo supportato per molto tempo è effettivamente -2 ^ 31 + 1 (-2147483647).|  
|TIMESTAMP|Quando un valore viene inserito in una colonna TIMESTAMP dal driver Paradox e quindi successivamente recuperato dalla colonna, il valore recuperato differiscano dal valore inserito da più di 1 secondo a causa dell'arrotondamento.|  
  
 Altre limitazioni sui tipi di dati sono reperibili [limitazioni del tipo di dati](../../odbc/microsoft/data-type-limitations.md).
