---
title: Valore elenco argomenti | Documenti Microsoft
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
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec4fd9498b01821bab2fa9216c809d0e25484ba7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="value-list-arguments"></a>Valore elenco argomenti
Argomento valore di un elenco è costituito da un elenco di valori delimitati da virgole da utilizzare per la corrispondenza. Non c'è l'argomento di elenco di un solo valore nelle funzioni di catalogo ODBC: il *TableType* argomento **SQLTables**. Impostazione *TableType* a un puntatore null è lo stesso come se è impostato su SQL_ALL_TABLE_TYPES, che enumera tutti i membri dell'elenco dei valori possibili. Questo argomento non è interessato dall'attributo di istruzione SQL_ATTR_METADATA_ID. Per ulteriori informazioni, vedere il [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) descrizione della funzione.
