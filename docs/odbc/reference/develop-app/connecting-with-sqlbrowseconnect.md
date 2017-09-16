---
title: Connessione con SQLBrowseConnect | Documenti Microsoft
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
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f2f1f3b183810e52f59945b7bc1888421cf48fc6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-with-sqlbrowseconnect"></a>Connessione con SQLBrowseConnect
**SQLBrowseConnect**, ad esempio **SQLDriverConnect**, utilizza una stringa di connessione. Tuttavia, utilizzando **SQLBrowseConnect**, un'applicazione può costruire una stringa di connessione completa in fase di esecuzione. In questo modo, l'applicazione può eseguire due operazioni:  
  
-   Compilare finestre di dialogo per la richiesta di queste informazioni, mantenendo in tal modo controllo sulla relativa "aspetto."  
  
-   Esplorare il sistema per individuare origini dati che possano essere utilizzate da un driver specifico, possibilmente in diversi passaggi. L'utente, ad esempio, potrebbe esplorare innanzitutto la rete per individuare i server e, dopo averne scelto uno, esplorare il server per individuare i database accessibili dal driver.  
  
 L'applicazione chiama **SQLBrowseConnect** e passa una stringa di connessione, nota come il *passare una stringa di connessione richiesta* che specifica un driver o l'origine dati. Il driver restituisce una stringa di connessione, nota come il *passare una stringa di connessione, risultato* che contiene le parole chiave, i valori possibili (se la parola chiave accetta un set di valori discreto) e nomi descrittivi. L'applicazione crea una finestra di dialogo con i nomi descrittivi e richiede l'immissione di valori. Quindi compila una nuova stringa di connessione richiesta Sfoglia da questi valori e restituisce l'oggetto per il driver con un'altra chiamata a **SQLBrowseConnect**.  
  
 Poiché le stringhe di connessione vengono passate avanti e indietro, il driver può fornire diversi livelli di esplorazione tramite la restituzione di una nuova stringa di connessione quando l'applicazione viene restituito quello precedente. Ad esempio, la prima volta un'applicazione chiama **SQLBrowseConnect**, il driver potrebbe restituire parole chiave per richiedere all'utente di un nome server. Quando l'applicazione viene restituito il nome del server, il driver potrebbe restituire parole chiave per richiedere all'utente per un database. Il processo di esplorazione sarebbe incompleta dopo l'applicazione ha restituito il nome del database.  
  
 Ogni volta che **SQLBrowseConnect** restituisce una stringa di connessione di risultato Sfoglia nuovo, verrà restituito SQL_NEED_DATA come il codice restituito. In questo modo l'applicazione che il processo di connessione non è completo. Fino a quando non **SQLBrowseConnect** restituisce SQL_SUCCESS, la connessione è in uno stato di dati necessario e non può essere utilizzato per altri scopi, ad esempio per impostare un attributo di connessione. L'applicazione può terminare la connessione di esplorazione processo chiamando **SQLDisconnect**.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Esempio di esplorazione di SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
