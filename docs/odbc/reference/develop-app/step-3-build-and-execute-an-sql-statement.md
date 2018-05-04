---
title: "Passaggio 3: Compilare ed eseguire un'istruzione SQL | Documenti Microsoft"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d3ee89477b2037f2eb11bdde1a6b08d53ad3065
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Passaggio 3: Compilare ed eseguire un'istruzione SQL
Il terzo passaggio è compilare ed eseguire un'istruzione SQL, come illustrato nella figura seguente. I metodi utilizzati per eseguire questo passaggio possono variare notevolmente. L'applicazione potrebbe richiedere all'utente di immettere un'istruzione SQL, un'istruzione SQL in base all'input di compilazione o utilizzare un'istruzione SQL a livello di codice. Per ulteriori informazioni, vedere [la costruzione di istruzioni SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Viene illustrata la creazione e l'esecuzione di un'istruzione SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Se l'istruzione SQL include parametri, l'applicazione li associa alle variabili di applicazione chiamando **SQLBindParameter** per ogni parametro. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Dopo l'istruzione SQL viene compilata e tutti i parametri associati, l'istruzione viene eseguita con **SQLExecDirect**. Se l'istruzione viene eseguita più volte, può essere preparato con **SQLPrepare** e verranno eseguiti con **SQLExecute**. Per ulteriori informazioni, vedere [l'esecuzione di un'istruzione](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 L'applicazione potrebbe essere inoltre evitare completamente l'esecuzione di un'istruzione SQL e chiamare invece una funzione per restituire un set di risultati contenente informazioni di catalogo, ad esempio le tabelle di colonne disponibili. Per ulteriori informazioni, vedere [utilizza dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Azione successiva dell'applicazione dipende dal tipo di istruzione SQL eseguita.  
  
|Tipo di istruzione SQL|Passare alla|  
|---------------------------|----------------|  
|**Selezionare** o del catalogo (funzione)|[Passaggio 4a: recuperare i risultati](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**AGGIORNAMENTO**, **eliminare**, o **INSERT**|[Passaggio 4b: recuperare il conteggio delle righe](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Tutte le altre istruzioni SQL|Passaggio 3: Compilare ed eseguire un'istruzione SQL (questo argomento) o [passaggio 5: eseguire il Commit della transazione](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
