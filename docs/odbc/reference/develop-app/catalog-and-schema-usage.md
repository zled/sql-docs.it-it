---
title: Catalogo e utilizzo dello Schema | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6653d44ad75fb9e2d1941a6d280ba0ec91dd275d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="catalog-and-schema-usage"></a>Catalogo e utilizzo dello Schema
Origini dati non supportano necessariamente i nomi di catalogo e lo schema come identificatori di nome di oggetto in tutte le istruzioni SQL. Origini dati potrebbero supportare i nomi di catalogo e lo schema in uno o più delle seguenti classi di istruzioni SQL: istruzioni Data Manipulation Language (DML), chiamate di procedure, istruzioni di definizione di tabella, le istruzioni di definizione di indice e definizione dei privilegi istruzioni. Per determinare le classi di istruzioni SQL in cui catalogo e lo schema è possibile utilizzare nomi, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_CATALOG_USAGE e SQL_SCHEMA_USAGE.
