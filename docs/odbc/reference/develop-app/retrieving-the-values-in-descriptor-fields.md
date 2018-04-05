---
title: Recupero di valori in campi di descrizione | Documenti Microsoft
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
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37efd70ccd8fa0ad5c6d4bb573eb1c158a3ec35b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Recupero di valori in campi di descrizione
Un'applicazione può chiamare **SQLGetDescField** per ottenere un singolo campo di un record del descrittore. **SQLGetDescField** fornisce l'accesso all'applicazione per tutti i campi di descrizione definiti in ODBC e anche campi definito dal driver.  
  
 **SQLGetDescRec** può essere chiamato per recuperare le impostazioni di più campi di descrizione che interessano il tipo di dati e archiviazione dei dati di colonna o parametro.
