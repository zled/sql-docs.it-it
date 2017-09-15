---
title: La funzione SQLInstallTranslator funzione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2b7efa21691627c346b6d3798ade158e946071e6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalltranslator-function"></a>La funzione SQLInstallTranslator (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.5, deprecato  
  
 **Riepilogo**  
 In ODBC 3.0 **la funzione SQLInstallTranslator** è stata sostituita da [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Le chiamate a **la funzione SQLInstallTranslator** verrà eseguito il mapping a **SQLInstallTranslatorEx**. Per ulteriori informazioni, vedere **SQLInstallTranslatorEx**.  
  
 **La funzione SQLInstallTranslator** restituirà FALSE se un'applicazione chiama in ODBC 3*x* gestione Driver con la *lpszInfFile* argomento impostato su un valore diverso da NULL. Il file Odbc.inf utilizzato in ODBC 2. *x* non è più supportata in ODBC 3*x*, anche per la compatibilità con le versioni precedenti.
