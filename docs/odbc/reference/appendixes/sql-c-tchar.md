---
title: SQL_C_TCHAR | Documenti Microsoft
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
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f2367dcae307e3152005c1bb47885a274c6cc0a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
L'identificatore del tipo SQL_C_TCHAR non identificare effettivamente un tipo di dati. è una macro che esiste all'interno del file di intestazione per la conversione Unicode. Viene sostituito con SQL_C_CHAR o SQL_C_WCHAR a seconda dell'impostazione di UNICODE **#define**. È utile per un'applicazione di trasferimento dei dati di tipo carattere che viene compilati come un'applicazione Unicode e ANSI.
