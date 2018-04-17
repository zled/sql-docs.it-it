---
title: Sequenza di record di stato | Documenti Microsoft
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
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a45a5be0c99dd6389fd060cc53f5140c5e7c263
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sequence-of-status-records"></a>Sequenza di record di stato
Se vengono restituiti due o più record di stato, il gestore dei Driver e il driver classificarli in base alle regole seguenti. Il record con il valore più alto è il primo record. L'origine di un record (gestione Driver, driver, gateway e così via) non viene considerato quando i record di rango.  
  
-   **Errori** record di stato che descrivono gli errori sono il rango più alto. Tra i record degli errori, i record che indicano un errore di transazione o di un errore di transazione possibili outrank tutti gli altri record. Se due o più record di descrivere la stessa condizione di errore, definiti dalla specifica CLI di gruppo aprire (classi 03 tramite HZ) SQLSTATE outrank SQLSTATE definite da ODBC e definito dal driver.  
  
-   **I valori dei dati non definito dall'implementazione** record di stato che descrivono definiti dal driver i valori dei dati di n (classe 02) è il secondo classificazione più elevata.  
  
-   **Avvisi** record di stato che descrivono gli avvisi (classe 01) hanno la priorità più bassa. Se due o più record descrivono la stessa condizione di avviso, di avviso SQLSTATE definiti dalla specifica CLI di gruppo aprire outrank SQLSTATE definite da ODBC e definito dal driver.  
  
 Se sono presenti due o più record con il valore più alto, non viene specificato di record che è il primo record. Non è definito l'ordine di tutti gli altri record. In particolare, poiché gli avvisi potrebbero apparire prima di errori, le applicazioni dovrebbero verificare tutti i record di stato quando una funzione restituisce un valore diverso da SQL_SUCCESS.
