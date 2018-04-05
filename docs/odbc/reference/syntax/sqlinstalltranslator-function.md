---
title: La funzione SQLInstallTranslator funzione | Documenti Microsoft
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
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eeb4c73651b0d32311788ebd2149fdf6cd055b04
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlinstalltranslator-function"></a>La funzione SQLInstallTranslator (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.5, deprecato  
  
 **Riepilogo**  
 In ODBC 3.0 **la funzione SQLInstallTranslator** è stata sostituita da [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Le chiamate a **la funzione SQLInstallTranslator** verrà eseguito il mapping a **SQLInstallTranslatorEx**. Per ulteriori informazioni, vedere **SQLInstallTranslatorEx**.  
  
 **La funzione SQLInstallTranslator** restituirà FALSE se un'applicazione chiama in ODBC 3*x* gestione Driver con la *lpszInfFile* argomento impostato su un valore diverso da NULL. Il file Odbc.inf utilizzato in ODBC 2. *x* non è più supportata in ODBC 3*x*, anche per la compatibilità con le versioni precedenti.
