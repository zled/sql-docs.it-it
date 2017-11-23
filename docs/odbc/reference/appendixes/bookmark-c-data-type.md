---
title: Tipo di dati C a segnalibro | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 698e450fbb816c5fb7e3caf3786f4b8d469af50c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="bookmark-c-data-type"></a>Tipo di dati C a segnalibro
Il tipo di dati C segnalibro consente a un'applicazione recuperare un segnalibro. I tipi di segnalibro C vengono utilizzati solo per recuperare i valori di segnalibro che possono essere una variabile di lunghezza. non devono essere convertiti in altri tipi di dati. Un'applicazione recupera un segnalibro dalla colonna 0 del risultato impostata con **SQLBulkOperations** (con un'operazione di SQL_ADD), **SQLFetch**, **SQLFetchScroll**, o **SQLGetData**. Per ulteriori informazioni, vedere [segnalibri](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 Nella tabella seguente elenca il valore di *CType* per il tipo di dati C segnalibro, il tipo di dati C ODBC che implementa il tipo di dati C segnalibro e la definizione dei dati di tipo da SQL. H.  
  
> [!NOTE]  
>  Il tipo di dati SQL_C_BOOKMARK è stato deprecato. ODBC 3*x* applicazioni non devono utilizzare SQL_C_BOOKMARK. ODBC 3*x* driver devono supportare SQL_C_BOOKMARK solo se si desidera utilizzare ODBC 2. *x* applicazioni che lo utilizzano. Gestione Driver mappata SQL_C_VARBOOKMARK SQL_C_BOOKMARK quando un'applicazione rispetto a una ODBC 2. *x* driver.  
  
|Identificatore di tipo C|Typedef di ODBC C|Tipo C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Deprecato)|SEGNALIBRO|unsigned long integer|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
