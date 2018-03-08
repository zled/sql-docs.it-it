---
title: "Interoperabilità | Documenti Microsoft"
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b797bcf1e8e5521ea2b4fd57a68969b3f04e802d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="interoperability"></a>Interoperabilità
*Interoperabilità* è la possibilità di una singola applicazione di operare con molti DBMS diversi. La necessità di scrivere applicazioni interoperabili generiche è uno dei fattori principali per lo sviluppo di ODBC. Tuttavia, interoperabilità non è un semplice percorso seguito da "non interoperabile" a "tutto intercambiabili". Il percorso dispone di molti branch, e ciascuna richiede compromessi tra le funzionalità, velocità, la complessità del codice e tempi di sviluppo.  
  
 Diverse operazioni per il processo di scrittura di un'applicazione di interoperabilità:  
  
1.  Decidere se l'applicazione utilizzerà ODBC.  
  
2.  Scelta di un livello di interoperabilità e decidere quali vantaggi e svantaggi sono necessari per raggiungere tale livello.  
  
3.  Scrittura di codice di interoperabilità e il relativo test massima.  
  
 Si noti che l'interoperabilità è principalmente il dominio del writer dell'applicazione. I driver sono progettati per funzionare con un singolo DBMS e, per definizione, non sono interoperativi. Essi svolgono un ruolo nell'interoperabilità implementando correttamente e l'esposizione di ODBC in un singolo DBMS.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [La risposta è ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Scelta di un livello di interoperabilità](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Determinazione dei DBMS e dei driver di destinazione](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considerazione delle funzionalità di database da usare](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Lunghezza del ciclo del prodotto](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Scrittura di un'applicazione interoperativa](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Test delle applicazioni interoperative](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
