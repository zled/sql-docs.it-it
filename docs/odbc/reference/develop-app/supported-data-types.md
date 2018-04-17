---
title: Tipi di dati supportati | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bcac33a3e45509591f46d8e340712ae2f30b2f55
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supported-data-types"></a>Tipi di dati supportati
I tipi di dati supportati da DBMS variano notevolmente. Un'applicazione può determinare i nomi e le caratteristiche dei tipi di dati supportati chiamando **SQLGetTypeInfo**. A causa delle ampie differenze nei nomi di tipi di dati, l'applicazione deve utilizzare i nomi dei tipi di dati restituiti da **SQLGetTypeInfo** in **CREATE TABLE** istruzioni. Per ulteriori informazioni, vedere [tipi di dati ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
