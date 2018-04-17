---
title: Controlli di valori di argomento | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b3e4c8772a8d6a6b2a00f6c8ffe4ab610d0e1ec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="argument-value-checks"></a>Controlli di valori di argomento
Gestione Driver controlla i seguenti tipi di argomenti. Se non diversamente specificato, gestione Driver restituisce SQL_ERROR errori nei valori dell'argomento.  
  
-   Handle di ambiente, connessione e di istruzione, in genere, non possono essere puntatori null. Gestione Driver non restituisca SQL_INVALID_HANDLE quando rileva un handle null.  
  
-   Richiesto come argomenti di puntatore, *OutputHandlePtr* in **SQLAllocHandle** e *Nomecursore* in **SQLSetCursorName**, non può essere puntatori null.  
  
-   Flag di opzione che non supportano valori specifici del driver devono essere un valore valido. Ad esempio, *operazione* in **SQLSetPos** deve essere SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE o SQL_ADD.  
  
-   Flag di opzione devono essere supportate nella versione di ODBC supportati dal driver. Ad esempio, *InfoType* in **SQLGetInfo** non può essere SQL_ASYNC_MODE, introdotta in ODBC 3.0, quando si chiama un driver ODBC 2.0.  
  
-   Numeri di colonna e di parametro devono essere maggiore di 0 o maggiore di o uguale a 0, a seconda della funzione. Il driver deve controllare il limite massimo di questi valori di argomento in base al set di risultati corrente o l'istruzione SQL.  
  
-   Gli argomenti di lunghezza/indicatore e argomenti di lunghezza del buffer di dati devono contenere i valori appropriati. Ad esempio, l'argomento che specifica la lunghezza di un nome di tabella in **SQLColumns** (*NameLength3*) deve essere SQL_NTS o un valore maggiore di 0; *BufferLength* in **SQLDescribeCol** deve essere maggiore o uguale a 0. Il driver potrebbe essere necessario anche controllare questi argomenti. Ad esempio, si potrebbe verificare che *NameLength3* è minore o uguale alla lunghezza massima di un nome di tabella nell'origine dati.
