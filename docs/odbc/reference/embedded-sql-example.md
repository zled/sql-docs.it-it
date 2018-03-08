---
title: Embedded SQL riportato di seguito | Documenti Microsoft
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
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 13890248b3e724f2a41db5a3425c62dc7635b63a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="embedded-sql-example"></a>Esempio di Embedded SQL
Il codice seguente è un programma SQL incorporato semplice, scritto in C. Il programma illustra molte, ma non l'intero incorporato tecniche di SQL. Il programma richiede l'immissione di un numero di ordine, recupera il numero cliente, venditore e lo stato dell'ordine e visualizza le informazioni recuperate sullo schermo.  
  
```  
int main() {  
   EXEC SQL INCLUDE SQLCA;  
   EXEC SQL BEGIN DECLARE SECTION;  
      int OrderID;         /* Employee ID (from user)         */  
      int CustID;            /* Retrieved customer ID         */  
      char SalesPerson[10]   /* Retrieved salesperson name      */  
      char Status[6]         /* Retrieved order status        */  
   EXEC SQL END DECLARE SECTION;  
  
   /* Set up error processing */  
   EXEC SQL WHENEVER SQLERROR GOTO query_error;  
   EXEC SQL WHENEVER NOT FOUND GOTO bad_number;  
  
   /* Prompt the user for order number */  
   printf ("Enter order number: ");  
   scanf_s("%d", &OrderID);  
  
   /* Execute the SQL query */  
   EXEC SQL SELECT CustID, SalesPerson, Status  
      FROM Orders  
      WHERE OrderID = :OrderID  
      INTO :CustID, :SalesPerson, :Status;  
  
   /* Display the results */  
   printf ("Customer number:  %d\n", CustID);  
   printf ("Salesperson: %s\n", SalesPerson);  
   printf ("Status: %s\n", Status);  
   exit();  
  
query_error:  
   printf ("SQL error: %ld\n", sqlca->sqlcode);  
   exit();  
  
bad_number:  
   printf ("Invalid order number.\n");  
   exit();  
}  
```  
  
 Si noti quanto segue su questo programma:  
  
-   **Ospitare variabili** vengono dichiarate le variabili di host in una sezione racchiusa il **iniziare sezione dichiarare** e **sezione dichiarare fine** parole chiave. Ogni nome di variabile host è preceduto dai due punti (:) quando viene visualizzato in un'istruzione SQL. I due punti consente precompilati distinguere tra le variabili di host e oggetti di database quali tabelle e colonne, che hanno lo stesso nome.  
  
-   **Tipi di dati** i tipi di dati supportati da un sistema DBMS e un linguaggio host possono essere molto diversi. Ciò influisce su variabili host perché si svolgono un ruolo doppio. Una parte, le variabili di host sono variabili di programma, dichiarato e modificati da istruzioni del linguaggio host. D'altra parte, vengono utilizzati nelle istruzioni SQL incorporate per recuperare i dati di database. Se è presente alcun tipo di linguaggio host che corrisponde a un tipo di dati DBMS, DBMS converte automaticamente i dati. Tuttavia, poiché ogni sistema DBMS ha regole e peculiarità associata al processo di conversione, i tipi di variabile host devono essere scelti attentamente.  
  
-   **Gestione degli errori** DBMS il report errori di run-time per il programma di applicazioni tramite un SQL Communications Area o SQLCA. Nell'esempio di codice precedente, la prima istruzione SQL incorporata è SQLCA INCLUDONO. In questo modo il precompilatore per includere la struttura SQLCA nel programma. Ciò è necessario ogni volta che il programma elaborerà gli errori restituiti dal sistema DBMS. Il WHENEVER... Istruzione GOTO indica precompilati per generare il codice di gestione degli errori che si verifica rami da un'etichetta specifica quando un errore.  
  
-   **Singleton selezionare** l'istruzione utilizzata per restituire i dati è un'istruzione SELECT singleton, ovvero, restituisce solo una singola riga di dati. L'esempio di codice, pertanto, non dichiarare o utilizzare i cursori.
