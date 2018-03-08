---
title: Marcatori di parametro di associazione | Documenti Microsoft
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
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f465e072b7ca7f2b551778eec67f1893e3875f28
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="binding-parameter-markers"></a>Marcatori di parametro di associazione
L'applicazione associa parametri chiamando **SQLBindParameter**. **SQLBindParameter** associa un parametro alla volta. Con questa soluzione, l'applicazione specifica quanto segue:  
  
-   Il numero di parametro. I parametri sono numerati in ordine crescente di parametro nell'istruzione SQL, a partire dal numero 1. Mentre è consentito specificare un numero di parametro che è superiore rispetto al numero di parametri nell'istruzione SQL, il valore del parametro sarà ignorato durante l'esecuzione dell'istruzione.  
  
-   Il tipo di parametro (input, input/output o di output). Ad eccezione di parametri nelle chiamate di procedura, tutti i parametri sono parametri di input. Per ulteriori informazioni, vedere [parametri di procedura](../../../odbc/reference/develop-app/procedure-parameters.md), più avanti in questa sezione.  
  
-   La C byte, l'indirizzo e tipo lunghezza dei dati della variabile è associato al parametro. Il driver deve essere in grado di convertire i dati dal tipo di dati C per il tipo di dati SQL o viene restituito un errore. Per un elenco delle conversioni supportate, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) appendice d: tipo di dati.  
  
-   Il tipo di dati SQL, precisione e scala del parametro stesso.  
  
-   L'indirizzo di un buffer di lunghezza/indicatore. Fornisce la lunghezza in byte di dati binari o character, specifica che i dati sono NULL o specifica che i dati verranno inviati con **SQLPutData**. Per ulteriori informazioni, vedere [tramite valori di lunghezza/indicatore](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Ad esempio, il codice seguente viene associato *venditore* e *CustID* ai parametri per le colonne venditore e CustID. Poiché *venditore* contiene i dati di tipo carattere, sono a lunghezza variabile, il codice specifica la lunghezza in byte di *venditore* (11) e associa *SalesPersonLenOrInd* per contiene la lunghezza in byte dei dati in *venditore*. Queste informazioni non sono necessarie per *CustID* perché contiene dati integer, che è di lunghezza fissa.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 Quando **SQLBindParameter** viene chiamato, il driver queste informazioni vengono memorizzate nella struttura per l'istruzione. Quando viene eseguita l'istruzione, Usa le informazioni per recuperare i dati del parametro e inviarlo all'origine dati.  
  
> [!NOTE]  
>  In ODBC 1.0, sono stati associati parametri **SQLSetParam**. Gestione Driver viene eseguito il mapping tra le chiamate **SQLSetParam** e **SQLBindParameter**, a seconda delle versioni di ODBC utilizzata dall'applicazione e del driver.
