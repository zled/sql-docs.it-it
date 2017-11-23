---
title: Architettura del driver | Documenti Microsoft
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC], architecture
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a8583c514ecaef5d85971c0c981427547574c4a7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="driver-architecture"></a>Architettura del driver
Architettura del driver può essere suddiviso in due categorie, a seconda di quali processi software istruzioni SQL:  
  
-   **Driver basati su file** il driver accede direttamente i dati fisici. In questo caso, il driver funge sia driver origine dati. vale a dire elabora chiamate ODBC e istruzioni SQL. Ad esempio, dBASE driver sono driver basati su file dBASE non includono che un motore di database autonomo, il driver può essere utilizzato. È importante notare che gli sviluppatori di driver basati su file è necessario scrivere i propri motori di database.  
  
-   **Driver basati su DBMS** il driver accede ai dati fisici tramite un motore di database separato. In questo caso il driver elabora solo chiamate ODBC; passa istruzioni SQL per motore di database per l'elaborazione. Ad esempio, il driver Oracle è driver basati su DBMS perché Oracle è un motore di database autonomo, che usa il driver. In cui risiede il motore di database non ha importanza. Può risiedere nella stessa macchina del driver o un altro computer della rete. può anche essere effettuato l'accesso tramite un gateway.  
  
 Architettura del driver è in genere interessano solo per gli sviluppatori di driver; architettura del driver in genere non esegue, ovvero è rilevante per l'applicazione. Tuttavia, l'architettura può influire sulle se un'applicazione può utilizzare SQL DBMS specifici. Ad esempio, Microsoft Access fornisce un motore di database autonomo. Se un driver Microsoft Access è basata su DBMS, accede ai dati tramite il motore, l'applicazione è possibile passare le istruzioni SQL di Microsoft Access al motore di elaborazione.  
  
 Tuttavia, se il driver è basata su file, ovvero, ovvero un motore proprietario che accede direttamente il file con estensione mdb di Microsoft® Access, qualsiasi tentativo di passare le istruzioni SQL specifici di Microsoft Access al motore di possono causare errori di sintassi. Il motivo è che il motore proprietario è probabile che implementare solo ODBC SQL.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Driver basati su file](../../odbc/reference/file-based-drivers.md)  
  
-   [Driver basati su DBMS](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Esempio di rete](../../odbc/reference/network-example.md)  
  
-   [Altre architetture di driver](../../odbc/reference/other-driver-architectures.md)
