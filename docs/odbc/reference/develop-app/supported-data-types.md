---
title: Tipi di dati supportati | Documenti Microsoft
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
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d76b98635cdc183f08f205374f8e7e0e66a4cb5f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="supported-data-types"></a>Tipi di dati supportati
I tipi di dati supportati da DBMS variano notevolmente. Un'applicazione può determinare i nomi e le caratteristiche dei tipi di dati supportati chiamando **SQLGetTypeInfo**. A causa delle ampie differenze nei nomi di tipi di dati, l'applicazione deve utilizzare i nomi dei tipi di dati restituiti da **SQLGetTypeInfo** in **CREATE TABLE** istruzioni. Per ulteriori informazioni, vedere [tipi di dati ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).

