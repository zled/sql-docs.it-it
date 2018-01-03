---
title: La funzione SQLInstallTranslator Mapping | Documenti Microsoft
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
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a4e0ce6bde70b75398ca8a9ad9e8880ec3fb500e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlinstalltranslator-mapping"></a>La funzione SQLInstallTranslator Mapping
Quando un'applicazione ODBC 2. *x* applicazione chiama **la funzione SQLInstallTranslator** tramite un'applicazione ODBC 3*x* driver, Driver Manager viene eseguito il mapping della chiamata a **SQLInstallTranslatorEx**. Un'applicazione non deve chiamare **la funzione SQLInstallTranslator** in ODBC 3*x* gestione Driver con la *lpszInfFile* argomento impostato su un valore diverso da NULL. ODBC. File INF utilizzato in ODBC 2. *x* non è più supportata in ODBC 3*x*, anche per la compatibilità con le versioni precedenti.
