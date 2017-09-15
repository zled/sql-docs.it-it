---
title: Applicazioni conformi agli standard e i driver | Documenti Microsoft
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
- standards-compliant applications and drivers [ODBC]
- ODBC drivers [ODBC], standards-compliant
- application features are standards-compliant [ODBC]
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1aba299d163aaf9ec14d86740e5d8aa91ddb7b3b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="standards-compliant-applications-and-drivers"></a>I driver e applicazioni conformi agli standard
Un driver o un'applicazione conforme agli standard è conforme a Open Specification CAE gruppo "Data Management: SQL chiamata a livello di interfaccia (CLI)" e ISO/IEC 9075-3:1995 interfaccia a livello di chiamata (E) (SQL/CLI).  
  
 ODBC 3*x* garantisce le funzionalità seguenti:  
  
-   Un'applicazione scritta per le specifiche Open Group e ISO CLI funzionerà con un'applicazione ODBC 3*x* driver o un driver conforme agli standard quando viene compilato con ODBC 3*x* i file di intestazione e collegato a ODBC 3*x* librerie, e quando accede al driver tramite ODBC 3*x* gestione Driver.  
  
-   Un driver di scrivere le specifiche Open Group e ISO CLI funzionerà con un'applicazione ODBC 3*x* o come applicazione conforme agli standard quando viene compilato con ODBC 3*x* file di intestazione e collegati con ODBC 3*x* librerie, e quando l'applicazione accede al driver tramite ODBC 3*x* gestione Driver.  
  
 I driver e applicazioni conformi agli standard vengono compilati con il flag di compilazione ODBC_STD.  
  
 Applicazioni conformi agli standard mostrano il comportamento seguente:  
  
-   Se un'applicazione conforme agli standard chiama **SQLAllocEnv** (che può verificarsi perché **SQLAllocEnv** è una funzione valida nella Open Group e ISO CLI), la chiamata viene eseguito il mapping a ** SQLAllocHandleStd** in fase di compilazione. Di conseguenza, in fase di esecuzione, l'applicazione chiama **SQLAllocHandleStd**. Nel corso dell'elaborazione della chiamata, gestione Driver imposta l'attributo di ambiente SQL_ATTR_ODBC_VERSION su SQL_OV_ODBC3. Una chiamata a **SQLAllocHandleStd** equivale a una chiamata a **SQLAllocHandle** con un *HandleType* di impostato su SQL_HANDLE_ENV e una chiamata a **SQLSetEnvAttr** impostare SQL_ATTR_ODBC_VERSION su SQL_OV_ODBC3.  
  
-   Se un'applicazione conforme agli standard chiama **SQLBindParam** (che può verificarsi perché **SQLBindParam** è una funzione valida nella Open Group e ISO CLI), ODBC 3*x* Gestione driver viene eseguito il mapping la chiamata alla chiamata di equivalenti in **SQLBindParameter**. (Vedere [SQLBindParam Mapping](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.)  
  
-   Per la compatibilità con ISO CLI, ODBC 3*x* file di intestazione contengono alias per i tipi di informazioni utilizzati nelle chiamate a **SQLGetInfo**. Un'applicazione conforme agli standard può utilizzare tali alias anziché ODBC 3*x* tipi di informazioni. Per ulteriori informazioni, vedere l'argomento successivo, [file di intestazione](../../../odbc/reference/develop-app/header-files.md).  
  
-   Un'applicazione conforme agli standard è necessario verificare che tutte le funzionalità supportate sono supportate nel driver che funzionerà con. Impostare l'attributo di istruzione SQL_ATTR_CURSOR_SCROLLABLE su SQL_SCROLLABLE e impostando l'attributo di istruzione SQL_ATTR_CURSOR_SENSITIVITY su SQL_INSENSITIVE o SQL_SENSITIVE sono funzionalità che sono disponibili come funzionalità facoltativa negli standard ma non vengono inclusi in ODBC 3*x* Core livello e pertanto potrebbero non essere supportati da tutti i 3 ODBC*x* driver. Se un'applicazione conforme agli standard utilizza queste funzionalità, è necessario verificare che il driver che funzionerà con supportarle.
