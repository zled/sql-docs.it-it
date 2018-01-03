---
title: Utilizzo di funzioni Concise | Documenti Microsoft
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
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fecf227f991a3c9c6edfb1ce29f5b3b781898e45
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="using-concise-functions"></a>Utilizzo di funzioni Concise
Alcune funzioni ODBC accedono in modo implicito a descrittori. Gli autori di applicazioni risultare molto più conveniente di chiamare il metodo **SQLSetDescField** o **SQLGetDescField**. Queste funzioni vengono chiamate *conciso* funzioni perché eseguono un numero di funzioni, inclusa l'impostazione o il recupero dei campi di descrizione. Alcune funzioni concisi consentono un'applicazione di impostare o recuperare diversi campi di descrizione correlati in una sola chiamata di funzione.  
  
 Funzioni concise possono essere chiamate senza prima recuperare un handle di descrittore per l'utilizzo come argomento. Queste funzioni con campi di descrizione associati all'handle di istruzione che vengono chiamati in.  
  
 Le funzioni concise **SQLBindCol** e **SQLBindParameter** associare una colonna o parametro impostando i campi di descrizione corrispondenti per i relativi argomenti. Ognuna di queste funzioni vengono eseguite più attività rispetto all'impostazione descrittori. **SQLBindCol** e **SQLBindParameter** fornire una specifica completa dell'associazione di una colonna di dati o un parametro dinamico. Un'applicazione può, tuttavia, modificare i singoli dettagli di un'associazione chiamando **SQLSetDescField** o **SQLSetDescRec** e può associare completamente da una serie di chiamate adatte a una colonna o parametro Queste funzioni.  
  
 Le funzioni concise **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, e  **SQLNumResultCols** recuperare i valori in campi di descrizione.  
  
 **SQLSetDescRec** e **SQLGetDescRec** assolvere conciso, con un'unica chiamata, impostare o ottenere più campi di descrizione che determinano il tipo di dati e archiviazione dei dati di colonna o parametro. **SQLSetDescRec** è un metodo efficace per modificare l'associazione di dati di colonna o parametro in un unico passaggio.  
  
 **SQLSetStmtAttr** e **SQLGetStmtAttr** fungono da funzioni concise in alcuni casi. (Vedere [campi di descrizione](../../../odbc/reference/develop-app/descriptor-fields.md).)
