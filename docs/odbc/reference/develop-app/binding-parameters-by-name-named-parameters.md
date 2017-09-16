---
title: Associazione dei parametri in base al nome (parametri denominati) | Documenti Microsoft
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
- named parameters [ODBC]
- binding parameters by name [ODBC]
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b3047d17ff1e9785e203b6be0ab48c7c27fd88d1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="binding-parameters-by-name-named-parameters"></a>Associazione dei parametri in base al nome (parametri denominati)
Alcuni DBMS consente di specificare i parametri da una stored procedure in base al nome anziché in base alla posizione nella chiamata di procedura. Tali parametri vengono chiamati *parametri denominati*. ODBC supporta l'utilizzo di parametri denominati. In ODBC i parametri denominati sono utilizzati solo nelle chiamate alle stored procedure e non possono essere utilizzati in altre istruzioni SQL.  
  
 Il driver controlla il valore del campo SQL_DESC_UNNAMED IPD per determinare se denominato vengono utilizzati i parametri. Se SQL_DESC_UNNAMED non è impostata su SQL_UNNAMED, il driver utilizza il nome del campo SQL_DESC_NAME del IPD per identificare il parametro. Per associare il parametro, un'applicazione può chiamare **SQLBindParameter** per specificare le informazioni di parametro e quindi possibile chiamare **SQLSetDescField** per impostare il campo SQL_DESC_NAME del IPD. Quando si utilizzano parametri denominati, l'ordine del parametro nella chiamata di procedura non è importante e numero di record del parametro viene ignorato.  
  
 La differenza tra parametri senza nome e i parametri denominati è la relazione tra il numero di record del descrittore e il numero di parametri nella procedura. Quando si utilizzano parametri senza nome, il primo marcatore di parametro è correlato al primo record nel descrittore di parametri, a sua volta è correlato al primo parametro (in ordine di creazione) nella chiamata di procedura. Quando si utilizzano parametri denominati, il primo marcatore di parametro è ancora correlato al primo record del descrittore del parametro, ma la relazione tra il numero di record del descrittore e il numero di parametro della procedura non esiste più. I parametri denominati non utilizzano il mapping del numero di record del descrittore per la posizione del parametro procedura; al contrario, il nome del record del descrittore viene eseguito il mapping al nome di parametro della routine.  
  
> [!NOTE]  
>  Se il popolamento automatico il IPD è abilitato, il driver popolerà il descrittore di modo che l'ordine dei record del descrittore corrisponderà all'ordine dei parametri nella definizione della stored procedure, anche se si utilizzano parametri denominati.  
  
 Se viene utilizzato un parametro denominato, tutti i parametri devono essere parametri denominati. Se un parametro non è un parametro denominato, nessuno dei parametri ca chiamarsi parametri. Se ci sono una combinazione di parametri denominati e i parametri senza nome, il comportamento sarà dipendente dal driver.  
  
 Ad esempio di parametri denominati, si supponga che un Server SQL stored procedure è stata definita come segue:  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 In questa procedura, il primo parametro, @title_id, ha un valore predefinito di 1. Un'applicazione può utilizzare il codice seguente per richiamare questa procedura in modo che specifichi un solo parametro dinamico. Questo parametro è un parametro denominato con il nome "@quote".  
  
```  
// Prepare the procedure invocation statement.  
SQLPrepare(hstmt, "{call test(?)}", SQL_NTS);  
  
// Populate record 1 of ipd.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                  30, 0, szQuote, 0, &cbValue);  
  
// Get ipd handle and set the SQL_DESC_NAMED and SQL_DESC_UNNAMED fields  
// for record #1.  
SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
// Assuming that szQuote has been appropriately initialized,  
// execute.  
SQLExecute(hstmt);  
```
