---
title: La funzione SQLInstallTranslator Mapping | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5de97b141f7ea2d1e3acf828f7d1b25bd77e0de7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlinstalltranslator-mapping"></a>La funzione SQLInstallTranslator Mapping
Quando un'applicazione ODBC 2. *x* applicazione chiama **la funzione SQLInstallTranslator** tramite un'applicazione ODBC 3*x* driver, Driver Manager viene eseguito il mapping della chiamata a **SQLInstallTranslatorEx**. Un'applicazione non deve chiamare **la funzione SQLInstallTranslator** in ODBC 3*x* gestione Driver con la *lpszInfFile* argomento impostato su un valore diverso da NULL. ODBC. File INF utilizzato in ODBC 2. *x* non è più supportata in ODBC 3*x*, anche per la compatibilità con le versioni precedenti.
