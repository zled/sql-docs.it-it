---
title: Recupero del descrittore gestisce | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 921d3e9bc76ff49b35b58d3b519a4adcc227d241
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="obtaining-descriptor-handles"></a>Recupero del descrittore gestisce
Un'applicazione ottiene l'handle di qualsiasi descrittore allocato in modo esplicito come argomento di output della chiamata a **SQLAllocHandle**. L'handle di un descrittore allocato in modo implicito viene ottenuto chiamando **SQLGetStmtAttr**.
