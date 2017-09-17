---
title: SQL_C_TCHAR | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b518868f3b6e77f9351877d57dc97cfee01a2c67
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlctchar"></a>SQL_C_TCHAR
L'identificatore del tipo SQL_C_TCHAR non identificare effettivamente un tipo di dati. è una macro che esiste all'interno del file di intestazione per la conversione Unicode. Viene sostituito con SQL_C_CHAR o SQL_C_WCHAR a seconda dell'impostazione di UNICODE **#define**. È utile per un'applicazione di trasferimento dei dati di tipo carattere che viene compilati come un'applicazione Unicode e ANSI.
