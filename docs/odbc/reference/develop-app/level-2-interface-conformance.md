---
title: "Livello 2 interfaccia conformità | Documenti Microsoft"
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
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c272637e15d95a09862170ec871274adb624c271
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="level-2-interface-conformance"></a>Conformità di interfaccia di livello 2
Il livello di conformità di interfaccia di livello 2 include la funzionalità di livello 1 interfaccia: livello di conformità e le funzionalità seguenti:  
  
|||  
|-|-|  
|201|Utilizzare nomi in tre parti di tabelle e viste. (Per ulteriori informazioni, vedere denominazione supporto funzionalità 101 a due parti in [la conformità a livello 1 interfaccia](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Vengono descritti i parametri dinamici, chiamando **SQLDescribeParam**.|  
|203|Utilizzare non solo parametri di input, ma anche i parametri di output e di input/output e valori dei risultati di stored procedure.|  
|204|Utilizzare i segnalibri, incluso il recupero di segnalibri, chiamando **SQLDescribeCol** e **SQLColAttribute** nella colonna numero 0; recupero basato su un segnalibro, chiamando **SQLFetchScroll** con il *FetchOrientation* argomento impostato su SQL_FETCH_BOOKMARK; e aggiornare, eliminare e il recupero da operazioni di segnalibro, chiamando **SQLBulkOperations** con il *Operazione* argomento impostato su SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK o SQL_FETCH_BY_BOOKMARK.|  
|205|Recuperare informazioni avanzate sul dizionario dei dati, chiamando **SQLColumnPrivileges**, **SQLForeignKeys**, e **SQLTablePrivileges**.|  
|206|Utilizzare le funzioni ODBC anziché istruzioni SQL per eseguire operazioni di database aggiuntive chiamando **SQLBulkOperations** con SQL_ADD, o **SQLSetPos** con SQL_DELETE o SQL_UPDATE. (Supporto per le chiamate a **SQLSetPos** con il *LockType* argomento impostato su SQL_LOCK_EXCLUSIVE o SQL_LOCK_UNLOCK non è una parte dei livelli di conformità, ma è una funzionalità facoltativa.)|  
|207|Abilitare l'esecuzione asincrona delle funzioni ODBC per le singole istruzioni specificate.|  
|208|Ottenere la colonna SQL_ROWVER identificazione delle righe delle tabelle, chiamando **SQLSpecialColumns**. (Per ulteriori informazioni, vedere il supporto per **SQLSpecialColumns** con il *IdentifierType* argomento impostato su SQL_BEST_ROWID come funzionalità 20 nel [Core interfaccia conformità](../../../odbc/reference/develop-app/core-interface-conformance.md) .)|  
|209|Impostare l'attributo di istruzione SQL_ATTR_CONCURRENCY su almeno un valore diverso da SQL_CONCUR_READ_ONLY.|  
|210|La possibilità di timeout richiesta di accesso e le query SQL (SQL_ATTR_LOGIN_TIMEOUT e SQL_ATTR_QUERY_TIMEOUT).|  
|211|La possibilità di modificare il livello di isolamento predefinito; la possibilità di eseguire transazioni con il livello di isolamento "serializzabile".|
