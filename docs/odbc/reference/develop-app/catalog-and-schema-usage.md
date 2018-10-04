---
title: Catalogo e utilizzo dello Schema | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9476f4f928890514354f97ce604f871bd8a06d11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702829"
---
# <a name="catalog-and-schema-usage"></a>Utilizzo del catalogo e dello schema
Origini dati non supportano necessariamente i nomi di catalogo e lo schema come identificatori di nome di oggetto in tutte le istruzioni SQL. Origini dati potrebbero supportare nomi di catalogo e lo schema in uno o più delle seguenti classi di istruzioni SQL: istruzioni Data Manipulation Language (DML), le chiamate di procedure, istruzioni di definizione di tabella, istruzioni per la definizione dell'indice e definizione dei privilegi istruzioni. Per determinare le classi di istruzioni SQL in quale catalogo e lo schema è possibile usare i nomi, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_CATALOG_USAGE e SQL_SCHEMA_USAGE.
