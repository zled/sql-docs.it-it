---
title: Valore elenco argomenti | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14c78f543f959e091e52db6881d49e4221667273
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="value-list-arguments"></a>Valore elenco argomenti
Argomento valore di un elenco è costituito da un elenco di valori delimitati da virgole da utilizzare per la corrispondenza. Non c'è l'argomento di elenco di un solo valore nelle funzioni di catalogo ODBC: il *TableType* argomento **SQLTables**. Impostazione *TableType* a un puntatore null è lo stesso come se è impostato su SQL_ALL_TABLE_TYPES, che enumera tutti i membri dell'elenco dei valori possibili. Questo argomento non è interessato dall'attributo di istruzione SQL_ATTR_METADATA_ID. Per ulteriori informazioni, vedere il [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) descrizione della funzione.
