---
title: Le istruzioni per la generazione di risultati e senza risultati | Documenti Microsoft
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
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cc68c7ca0528d2a8af2af5d33d92fb8bf92c64f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="result-generating-and-result-free-statements"></a>Istruzioni per la generazione di risultati e senza risultati
Istruzioni SQL possono essere ad accoppiamento suddivisi in cinque categorie seguenti:  
  
-   **Causare la generazione di Set di istruzioni** si tratta di istruzioni SQL che generano un set di risultati. Ad esempio, un **selezionare** istruzione.  
  
-   **Le istruzioni di generazione di conteggio di righe** si tratta di istruzioni SQL che generano un numero di righe interessate. Ad esempio, un **aggiornamento** o **eliminare** istruzione.  
  
-   **Istruzioni Data Definition Language (DDL)** si tratta di istruzioni SQL che modificano la struttura del database. Ad esempio, **CREATE TABLE** o **DROP INDEX**.  
  
-   **Le istruzioni di modifica contesto** si tratta di istruzioni SQL che modificano il contesto di un database. Ad esempio, il **utilizzare** e **impostare** istruzioni in SQL Server.  
  
-   **Istruzioni amministrative** si tratta di istruzioni SQL utilizzate per scopi amministrativi in un database. Ad esempio, **GRANT** e **revocare**.  
  
 Istruzioni SQL nelle prime due categorie sono noti come *istruzioni che generano risultati*. Le istruzioni SQL in tre categorie quest'ultime sono noti come *senza risultati istruzioni*. ODBC definisce la semantica di batch che includono istruzioni solo la generazione di risultati. Questa semantica varia notevolmente e è pertanto specifici dell'origine dati. Ad esempio, il driver SQL Server non supporta il trascinamento di un oggetto e che fa riferimento a o ricreare lo stesso oggetto di nello stesso batch. Pertanto, il termine *batch* utilizzato in questo manuale si riferisce solo ai batch di generazione di risultati di istruzioni.
