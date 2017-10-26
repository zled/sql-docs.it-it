---
title: Mapping SQLColAttributes | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d21d1a9a9565ad2c0accbebb716d0b24f18f854d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcolattributes-mapping"></a>Mapping di SQLColAttributes
Quando un'applicazione chiama **SQLColAttributes** tramite un'applicazione ODBC 3*x* driver, la chiamata a **SQLColAttributes** viene eseguito il mapping a **SQLColAttribute** come indicato di seguito:  
  
> [!NOTE]  
>  Il prefisso utilizzato *FieldIdentifier* valori in ODBC 3*x* è stato modificato da tali utilizzati in ODBC 2.* x*. Il prefisso è "SQL_DESC"; il prefisso precedente era "SQL_COLUMN".  
  
1.  Se l'applicazione è un'API ODBC 2. *x* applicazione *fDescType* è SQL_COLUMN_TYPE e il tipo restituito è un tipo DATETIME conciso, le mappe di gestione Driver la restituzione di valori per i codici di date, time e timestamp.  
  
2.  Se *fDescType* è SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE o SQL_COLUMN_COUNT, le chiamate di gestione Driver **SQLColAttribute** nel driver con la *FieldIdentifier* argomento mappato a SQL_DESC_NAME, SQL_DESC_NULLABLE o SQL_DESC_COUNT, come appropriato*.* Tutti gli altri valori di *fDescType* vengono passati al driver.  
  
 Un'applicazione ODBC 3*x* driver deve supportare tutti i 3 ODBC*x* *FieldIdentifiers* elencati per **SQLColAttribute**.  
  
 Un'applicazione ODBC 3*x* driver deve supportare SQL_COLUMN_PRECISION e SQL_DESC_PRECISION, SQL_COLUMN_SCALE e SQL_DESC_SCALE, SQL_COLUMN_LENGTH e SQL_DESC_LENGTH. Questi valori sono diversi perché precisione, scala e lunghezza vengono definite in modo diverso in ODBC 3*x* rispetto alle API ODBC 2.* x*. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.

