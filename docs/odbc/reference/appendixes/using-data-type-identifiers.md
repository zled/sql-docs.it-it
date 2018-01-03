---
title: Utilizzo di identificatori di tipo dati | Documenti Microsoft
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
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0831a683cca3814712697ebbafffcfcdd1f3f86d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="using-data-type-identifiers"></a>Utilizzando gli identificatori di tipo di dati
Le applicazioni utilizzano gli identificatori di tipo di dati in due modi: per descrivere i buffer per il driver e recuperare i metadati relativi set di risultati dal driver in modo che sia possibile stabilire il tipo di C memorizza nel buffer da utilizzare per archiviare i dati. Le applicazioni chiamano le funzioni seguenti per eseguire queste attività:  
  
-   **SQLBindParameter**, **SQLBindCol**, e **SQLGetData** , per descrivere il tipo di dati C di buffer dell'applicazione.  
  
-   **SQLBindParameter** , per descrivere il tipo di dati SQL di parametri dinamici.  
  
-   **SQLColAttribute** e **SQLDescribeCol** , per recuperare i tipi di dati SQL di colonne del set di risultati.  
  
-   **SQLDescribeParameter** , per recuperare i tipi di dati SQL di parametri.  
  
-   **SQLColumns**, **SQLProcedureColumns**, e **SQLSpecialColumns** , per recuperare i tipi di dati SQL di varie informazioni sullo schema  
  
-   **SQLGetTypeInfo** , per recuperare un elenco di tipi di dati supportati  
  
 Gli identificatori di tipo di dati vengono archiviati nel campo SQL_DESC_CONCISE_TYPE di un descrittore. Le funzioni di descrittore **SQLSetDescField** e **SQLSetDescRec** può essere utilizzato con i tipi appropriati per eseguire le attività elencate nell'elenco precedente. Per ulteriori informazioni, vedere [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
