---
title: Dati Unicode | Documenti Microsoft
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
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3bb3278fe83922aee29aa8348d32b3fbc757511
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-data"></a>Dati Unicode
Per descrivere i dati che si trovano in formato Unicode in modo nativo nel sistema DBMS sono disponibili i tipi di dati Unicode di SQL. Un tipo di dati Unicode C viene fornito per consentire a un'applicazione associare dati a un buffer di Unicode. Gestione Driver può convertire i dati da un tipo di Unicode C (SQL_C_WCHAR) per rendere una funzione con un driver ANSI.  
  
 Un database ODBC 3.0 o 2. *x* applicazione eseguirà sempre l'associazione ai tipi di dati ANSI. Per ottenere prestazioni ottimali, un'applicazione di ODBC 3.5 (o versione successiva) deve essere associato al tipo di dati C ANSI se il tipo di colonna SQL ANSI e deve essere associato al tipo di dati Unicode C se il tipo di colonna SQL è in formato Unicode.  
  
 Gli indicatori di tipo SQL Unicode sono SQL_WCHAR, SQL_WVARCHAR e SQL_WLONGVARCHAR. I dati SQL_WCHAR ha una lunghezza di stringa fissa, mentre SQL_WVARCHAR con lunghezza variabile con un massimo di dichiarata SQL_WLONGVARCHAR con lunghezza variabile con un massimo che dipende dall'origine dati.  
  
 L'indicatore di tipo C Unicode è SQL_C_WCHAR. Questo è il valore predefinito per ognuno degli indicatori di tipo SQL Unicode. Tutti i tipi SQL può essere convertiti in SQL_C_WCHAR, e SQL_C_WCHAR può essere convertito in tutti i tipi SQL. Un'applicazione può recuperare i dati in uno dei tre modi:  
  
-   Recuperare i dati come SQL_C_CHAR.  
  
-   Recuperare i dati come SQL_C_WCHAR.  
  
-   Dichiarare i dati come SQL_C_TCHAR. Si tratta di una macro che inserisce SQL_C_WCHAR se l'applicazione viene compilata come un'applicazione Unicode o inserisce SQL_C_CHAR se viene compilato come applicazione ANSI.  
  
 SQL_C_TCHAR viene dichiarata in una funzione come segue:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Quando l'applicazione viene compilata come un'applicazione Unicode, il *ValueType* argomento verrà modificato da SQL_C_TCHAR a SQL_C_WCHAR. Quando viene compilata l'applicazione come applicazione ANSI, il *ValueType* argomento verrà modificato a SQL_C_CHAR.  
  
 I driver di Unicode devono comunque supportare tipi di dati ANSI, tra cui SQL_CHAR. Se un'applicazione che utilizza un driver Unicode associa a SQL_CHAR, gestione Driver non eseguirà il mapping dei dati SQL_CHAR per SQL_WCHAR. Il driver Unicode è necessario accettare i dati SQL_CHAR.  
  
 Gestione Driver archivia driver e i nomi DSN in formato Unicode e ne esegue il mapping ad ANSI in base alle esigenze. Se un carattere Unicode non può essere mappato a un carattere ANSI (come può verificarsi se i caratteri da una tabella codici che non è la pagina di codice nativo del computer vengono utilizzati nei nomi DSN e driver), che non è stato possibile convertire i caratteri sono rappresentati dal sup carattere predefinito plied dal sistema.
