---
title: Parametri di procedura | Documenti Microsoft
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
- procedure parameters [ODBC]
ms.assetid: 54fd857e-d2cb-467d-bb72-121e67a8e88d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea30d30d66761e245a89fadd4bea37d6503c458b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="procedure-parameters"></a>Parametri di routine
I parametri nelle chiamate di procedura possono essere di input, input/output o i parametri di output. Ciò è diverso dai parametri di tutte le altre istruzioni SQL sono sempre i parametri di input.  
  
 Parametri di input vengono utilizzati per inviare i valori per la procedura. Si supponga, ad esempio, che la tabella di parti contiene colonne PartID, la descrizione e prezzo. La procedura InsertPart potrebbe essere un parametro di input per ogni colonna nella tabella. Ad esempio  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Un driver non deve modificare il contenuto di un buffer di input fino al **SQLExecDirect** o **SQLExecute** restituisce SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE o SQL_NO_DATA. Il contenuto del buffer di input non deve essere modificato mentre **SQLExecDirect** o **SQLExecute** restituisce SQL_NEED_DATA o SQL_STILL_EXECUTING.  
  
 Parametri di input/output vengono utilizzati sia per l'invio di valori alle procedure e recuperare valori da procedure. Utilizzando lo stesso parametro di input e un parametro di output tende a essere poco chiare e deve essere evitato. Si supponga, ad esempio, una stored procedure accetta un ID ordine e restituisce l'ID del cliente. Ciò può essere definito con un singolo parametro di input/output:  
  
```  
{call GetCustID(?)}  
```  
  
 Potrebbe essere preferibile utilizzare due parametri: un parametro di input per l'ID dell'ordine e un output o un parametro di input/output per l'ID del cliente:  
  
```  
{call GetCustID(?, ?)}  
```  
  
 I parametri di output vengono utilizzati per recuperare il valore restituito dalla routine e per recuperare valori da argomenti di routine. le procedure che restituiscono valori sono anche detto *funzioni*. Si supponga, ad esempio, il **GetCustID** procedure citate restituisce un valore che indica se è stato possibile trovare l'ordine. Nella chiamata seguente, il primo parametro è un parametro di output utilizzato per recuperare il valore restituito dalla routine, il secondo parametro è un parametro di input utilizzato per specificare l'ID dell'ordine e il terzo parametro è un parametro di output utilizzato per recuperare l'ID del cliente:  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Driver gestiscono i valori per l'input e di input/output parametri nelle procedure non in modo diverso rispetto ai parametri di input in altre istruzioni SQL. Quando viene eseguita l'istruzione, vengano recuperati i valori delle variabili associate a questi parametri e li inviano all'origine dati.  
  
 Dopo l'istruzione è stata eseguita, i driver di archiviano i valori restituiti di input/output e i parametri di output nelle variabili associate a tali parametri. Questi restituito non è garantito che i valori vengano impostati fino a dopo che sono stati recuperati tutti i risultati restituiti dalla procedura e **SQLMoreResults** ha restituito SQL_NO_DATA. Se l'esecuzione dell'istruzione genera un errore, il contenuto del buffer del parametro di input/output o buffer dei parametri di output è definito.  
  
 Un'applicazione chiama **SQLProcedure** per determinare se una stored procedure con un valore restituito. Chiama **SQLProcedureColumns** per determinare il tipo (valore restituito, input, input/output o di output) di ogni parametro di routine.
