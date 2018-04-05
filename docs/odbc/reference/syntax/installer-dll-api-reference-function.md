---
title: Programma di installazione nella DLL la funzione di riferimento all'API | Documenti Microsoft
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
- installer DLL [ODBC]
ms.assetid: 47fcadc3-f102-4989-9ee7-a1c65233142a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 614548110102e21cdd9f4bd5ba01f85aff6a6c55
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="installer-dll-api-reference-function"></a>Programma di installazione nella DLL la funzione API Reference
In questa sezione viene descritta la sintassi delle funzioni DLL API del programma di installazione. Il programma di installazione costituito da 20 funzioni API DLL. Tre di queste funzioni, **SQLGetTranslator**, **SQLRemoveDSNFromIni**, e **SQLWriteDSNToIni**, vengono chiamati solo da file DLL di installazione. Le altre funzioni vengono chiamate dai programmi di installazione e amministrazione.  
  
 Ogni funzione è contrassegnata con la versione di ODBC in cui è stato introdotto.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Funzione SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)  
  
-   [Funzione SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)  
  
-   [Funzione SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)  
  
-   [Funzione SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)  
  
-   [Funzione SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)  
  
-   [Funzione SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)  
  
-   [Funzione SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)  
  
-   [Funzione SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)  
  
-   [Funzione SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)  
  
-   [Funzione SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)  
  
-   [Funzione SQLInstallTranslator](../../../odbc/reference/syntax/sqlinstalltranslator-function.md)  
  
-   [Funzione SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)  
  
-   [SQLManageDataSources (funzione)](../../../odbc/reference/syntax/sqlmanagedatasources.md)  
  
-   [Funzione SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)  
  
-   [Funzione SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)  
  
-   [Funzione SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)  
  
-   [Funzione SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)  
  
-   [Funzione SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)  
  
-   [Funzione SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)  
  
-   [Funzione SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)  
  
-   [Funzione SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)  
  
-   [Funzione SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)  
  
-   [Funzione SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)  
  
-   [Funzione SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)  
  
-   [Funzione SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)
