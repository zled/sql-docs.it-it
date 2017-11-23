---
title: Modifiche del comportamento e i driver ODBC 3. x | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7a5bcfea240af2477b3522f2baa849a6a5a6876
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Modifiche del comportamento e i driver ODBC 3. x
L'attributo di ambiente SQL_ATTR_ODBC_VERSION indica al driver se è necessario presentare ODBC 2. *x* comportamento o ODBC 3*x* comportamento. La modalità in cui è impostato l'attributo di ambiente SQL_ATTR_ODBC_VERSION dipende dall'applicazione. ODBC 3*x* le applicazioni devono chiamare **SQLSetEnvAttr** per impostare questo attributo dopo che chiamano **SQLAllocHandle** per allocare un handle di ambiente e prima di chiamare  **SQLAllocHandle** per allocare un handle di connessione. In caso di eseguire questa operazione, gestione Driver restituisce SQLSTATE HY010 (funzione di errore nella sequenza) alla chiamata a quest'ultimo **SQLAllocHandle**.  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle modifiche di comportamento e come un'applicazione funziona, vedere [modifiche del comportamento](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC 2. *x* applicazioni e ODBC 2. *x* applicazioni ricompilate con ODBC 3*x* file di intestazione non chiamano **SQLSetEnvAttr**. Tuttavia, possono chiamare **SQLAllocEnv** anziché **SQLAllocHandle** per allocare un handle di ambiente. Pertanto, quando l'applicazione chiama **SQLAllocEnv** in Gestione Driver, Driver Manager chiama **SQLAllocHandle** e **SQLSetEnvAttr** nel driver. Di conseguenza, ODBC 3*x* driver sempre possono contare su questo attributo viene impostato.  
  
 Se un'applicazione conforme agli standard compilato con il flag di compilazione ODBC_STD chiamate **SQLAllocEnv** (che può verificarsi perché **SQLAllocEnv** non è deprecato in ISO), la chiamata viene eseguito il mapping a  **SQLAllocHandleStd** in fase di compilazione. In fase di esecuzione, l'applicazione chiama **SQLAllocHandleStd**. Gestione Driver imposta l'attributo di ambiente SQL_ATTR_ODBC_VERSION su SQL_OV_ODBC3. Una chiamata a **SQLAllocHandleStd** equivale a una chiamata a **SQLAllocHandle** con un *HandleType* di impostato su SQL_HANDLE_ENV e una chiamata a **SQLSetEnvAttr** impostare SQL_ATTR_ODBC_VERSION su SQL_OV_ODBC3.  
  
 In alcune architetture di driver, è necessario per il driver venga visualizzato come un ODBC 2. *x* driver o un'applicazione ODBC 3*x* driver, a seconda della connessione. Il driver in questo caso potrebbe non risultare un driver, ma un livello che si trova tra gestione Driver e un altro driver. Ad esempio, potrebbe simulare un driver, ad esempio ODBC Spy. In un altro esempio, potrebbe agire come gateway, ad esempio EDA/SQL. Vengono visualizzati come un'applicazione ODBC 3*x* driver, driver di questo tipo deve essere in grado di esportare **SQLAllocHandle**e venga visualizzato come un ODBC 2. *x* driver, deve essere in grado di esportare **SQLAllocConnect**, **SQLAllocEnv**, e **SQLAllocStmt**. Quando un ambiente, connessione o l'istruzione deve essere allocata, gestione Driver controlla per vedere se il driver Esporta **SQLAllocHandle**. Perché il driver non, le chiamate di gestione Driver **SQLAllocHandle** nel driver. Se il driver collabora con un ODBC 2. *x* driver, il driver deve eseguire il mapping della chiamata a **SQLAllocHandle** a **SQLAllocConnect**, **SQLAllocEnv**, o  **SQLAllocStmt**, a seconda dei casi. Inoltre necessario non eseguire alcuna operazione con il **SQLSetEnvAttr** chiamare quando si comporta come un ODBC 2. *x* driver.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di dati datetime](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Compatibilità con le versioni precedenti dei tipi di dati C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Segnalibri di lunghezza fissa](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [Supporto di SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Restituzione di SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Chiamata di SQLSetPos per inserire i dati](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Caricamento per ordinale](../../../odbc/reference/appendixes/loading-by-ordinal.md)
