---
title: Utilizzo di identificatori di tipo Data | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6b8fa49f509c3442c83488ba1e0a5e4a2359d3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654947"
---
# <a name="using-data-type-identifiers"></a>Uso degli identificatori dei tipi di dati
Le applicazioni utilizzano gli identificatori di tipo di dati in due modi: per descrivere i relativi buffer sul driver e per recuperare metadati su set di risultati dal driver, in modo che sia possibile stabilire quale tipo di C memorizza nel buffer da utilizzare per archiviare i dati. Le applicazioni chiamano le funzioni seguenti per eseguire queste attività:  
  
-   **SQLBindParameter**, **SQLBindCol**, e **SQLGetData** , ovvero per descrivere il tipo di dati C di buffer dell'applicazione.  
  
-   **SQLBindParameter** , ovvero per descrivere il tipo di dati SQL di parametri dinamici.  
  
-   **SQLColAttribute** e **SQLDescribeCol** , per recuperare i tipi di dati SQL di colonne del set di risultati.  
  
-   **SQLDescribeParameter** , per recuperare i tipi di dati SQL di parametri.  
  
-   **SQLColumns**, **SQLProcedureColumns**, e **SQLSpecialColumns** , per recuperare i tipi di dati SQL di varie informazioni sullo schema  
  
-   **SQLGetTypeInfo** , per recuperare un elenco di tipi di dati supportati  
  
 Gli identificatori di tipo di dati vengono archiviati nel campo SQL_DESC_CONCISE_TYPE di un descrittore. Le funzioni di descrittore **SQLSetDescField** e **SQLSetDescRec** utilizzabile con i tipi appropriati per eseguire le attività elencate nell'elenco precedente. Per altre informazioni, vedere [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
