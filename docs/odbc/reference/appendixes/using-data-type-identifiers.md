---
title: Utilizzo di identificatori di tipo dati | Documenti Microsoft
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
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a43271157667e98dd9157edb3a2cfd0e85eeee4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907676"
---
# <a name="using-data-type-identifiers"></a>Utilizzando gli identificatori di tipo di dati
Le applicazioni utilizzano gli identificatori di tipo di dati in due modi: per descrivere i buffer per il driver e recuperare i metadati relativi set di risultati dal driver in modo che sia possibile stabilire il tipo di C memorizza nel buffer da utilizzare per archiviare i dati. Le applicazioni chiamano le funzioni seguenti per eseguire queste attività:  
  
-   **SQLBindParameter**, **SQLBindCol**, e **SQLGetData** , ovvero per descrivere il tipo di dati C di buffer dell'applicazione.  
  
-   **SQLBindParameter** , ovvero per descrivere il tipo di dati SQL di parametri dinamici.  
  
-   **SQLColAttribute** e **SQLDescribeCol** , per recuperare i tipi di dati SQL di colonne del set di risultati.  
  
-   **SQLDescribeParameter** , per recuperare i tipi di dati SQL di parametri.  
  
-   **SQLColumns**, **SQLProcedureColumns**, e **SQLSpecialColumns** , per recuperare i tipi di dati SQL di varie informazioni sullo schema  
  
-   **SQLGetTypeInfo** , per recuperare un elenco di tipi di dati supportati  
  
 Gli identificatori di tipo di dati vengono archiviati nel campo SQL_DESC_CONCISE_TYPE di un descrittore. Le funzioni di descrittore **SQLSetDescField** e **SQLSetDescRec** può essere utilizzato con i tipi appropriati per eseguire le attività elencate nell'elenco precedente. Per ulteriori informazioni, vedere [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
