---
title: Istruzioni SQL costruite in fase di esecuzione | Documenti Microsoft
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
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 76c05e6d7148ac11e25783caca575bee034dd872
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sql-statements-constructed-at-run-time"></a>Istruzioni SQL costruite in fase di esecuzione
Applicazioni che eseguono analisi ad hoc comunemente compilare istruzioni SQL in fase di esecuzione. Ad esempio, un foglio di calcolo potrebbe consentire a un utente di selezionare le colonne da cui recuperare i dati:  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 Un'altra classe di applicazioni che in genere crea istruzioni SQL in fase di esecuzione sono gli ambienti di sviluppo di applicazioni. Tuttavia, le istruzioni che creano sono hardcoded nell'applicazione in corso di sviluppo, in cui possono in genere essere ottimizzati e testati.  
  
 Le applicazioni che creare istruzioni SQL in fase di esecuzione possano offrono flessibilità per l'utente. Come si può notare nell'esempio precedente, che non supporta anche le operazioni comuni come **in** clausole, **ORDER BY** clausole o join, la costruzione di istruzioni SQL in fase di esecuzione è molto più complesso rispetto alle istruzioni a livello di codice. Inoltre, verifica di tali applicazioni è problematica, perché è possibile costruire un numero arbitrario di istruzioni SQL.  
  
 Uno svantaggio potenziale di creazione di istruzioni SQL in fase di esecuzione è che richiede più tempo per costruire un'istruzione di usare un'istruzione a livello di codice. Fortunatamente, raramente si tratta di un problema. Tali applicazioni tendono a essere elevato utilizzo di interfaccia utente e il tempo dedicato dall'applicazione di istruzioni SQL è generalmente di dimensioni ridotte rispetto all'ora in cui l'utente impiega immissione dei criteri.
