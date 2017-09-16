---
title: La dichiarazione dell'applicazione &#39; s ODBC versione | Documenti Microsoft
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
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 32bfeff983ef5dff4ebfe3e575bcf36e855184d0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="declaring-the-application39s-odbc-version"></a>La dichiarazione dell'applicazione &#39; s versione ODBC
Prima di un'applicazione alloca una connessione, è necessario impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION. Questo attributo indica che l'applicazione seguente ODBC 2. *x* o ODBC 3.* x* specifica quando si utilizzano gli elementi seguenti:  
  
-   **SQLSTATE**. Numero di valori SQLSTATE è diversi in ODBC 2. *x* e ODBC 3.* x*.  
  
-   **Date, Time e gli identificatori di tipo Timestamp**. La tabella seguente illustra gli identificatori di tipo per date, time e dati di tipo timestamp ODBC 2. *x* e ODBC 3.* x*.  
  
    |ODBC 2. *x*|ODBC 3. *x*|  
    |----------------|----------------|  
    |**Identificatori di tipo SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identificatori di tipo C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   *CatalogName***argomento SQLTables**.   In ODBC 2. *x*, i caratteri jolly ("%" e "_") nei *CatalogName* argomento vengono trattati letteralmente. In ODBC 3. *x*, vengono considerate come caratteri jolly. Di conseguenza, un'applicazione che segue l'API ODBC 2. *x* specifica non è possibile utilizzarle come escape non li quando vengono utilizzati come valori letterali e caratteri jolly. Un'applicazione che segue ODBC 3. *x* specifica è possibile utilizzare queste informazioni come caratteri jolly o utilizzare caratteri di escape e li utilizzi come valori letterali. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 ODBC 3*x* gestione Driver e ODBC 3*x* driver controllare la versione della specifica di ODBC in cui viene scritta un'applicazione e rispondere di conseguenza. Ad esempio, se è seguito dall'applicazione ODBC 2. *x* specifica e chiama **SQLExecute** prima di chiamare **SQLPrepare**, ODBC 3*x* gestione Driver restituisce SQLSTATE S1010 ( Errore nella sequenza funzione). Se l'applicazione segue ODBC 3*x* specifica, gestione Driver restituisce SQLSTATE HY010 (funzione di errore nella sequenza). Per ulteriori informazioni, vedere [compatibilità e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Applicazioni che seguono ODBC 3. *x* specifica è necessario utilizzare il codice condizionale per evitare di utilizzare funzionalità nuove per ODBC 3.* x* quando si lavora con ODBC 2.* x* driver. ODBC 2. *x* driver non supportano la funzionalità nuova in ODBC 3.* x* solo perché l'applicazione dichiara che segue ODBC 3.* x* specifica. Inoltre, ODBC 3. *x* driver non cessano supportare la funzionalità nuova in ODBC 3.* x* solo perché l'applicazione dichiara che segue l'API ODBC 2.* x* specifica.
