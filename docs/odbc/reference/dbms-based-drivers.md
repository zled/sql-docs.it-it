---
title: Driver basati su DBMS | Documenti Microsoft
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
- drivers [ODBC], DBMS-based drivers
- DBMS-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
ms.assetid: e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 09265543685ea8fd573ee20bea90093f920b6e49
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="dbms-based-drivers"></a>Driver basati su DBMS
Driver basati su DBMS vengono utilizzati con origini dati, ad esempio Oracle o SQL Server che forniscono un motore di database autonomo per il driver da utilizzare. Questi driver accedere ai dati fisici tramite il motore autonomo; ovvero sono inviare istruzioni SQL e recuperare i risultati dal motore.  
  
 Driver basati su DBMS di utilizzare un motore di database esistente, sono in genere più semplice da scrivere rispetto a driver basati su file. Anche se un driver basati su DBMS può essere facilmente implementato traducendo chiamate ODBC in chiamate API native, ciò comporta un driver più lento. Un modo migliore per implementare un driver basati su DBMS è utilizzare il protocollo di flusso dei dati sottostante, che viene in genere eseguita l'API nativa. Ad esempio, un driver di SQL Server deve utilizzare TDS (i dati di protocollo del flusso per SQL Server) anziché DB Library (l'API nativa per SQL Server). Un'eccezione a questa regola è quando ODBC è l'API nativa. Ad esempio, Watcom SQL è un motore autonomo che si trova nello stesso computer dell'applicazione e viene caricato direttamente perché il driver.  
  
 Driver basati su DBMS fungere da client in una configurazione client/server in cui l'origine dati funge da server. Nella maggior parte dei casi, il client (driver) e il server (origine dati) si trovano in computer diversi, anche se potrebbe risiedono nello stesso computer che eseguono un sistema operativo multitasking. Una terza possibilità è un *gateway,* che si trova tra il driver e l'origine dati. Un gateway è un componente software che causa un DBMS simile a un altro. Ad esempio, le applicazioni scritte per l'utilizzo di SQL Server accessibile anche dati DB2 tramite il Gateway di DB2 Decisionware Micro; Questo prodotto provoca DB2 simile a SQL Server.  
  
 Nella figura seguente mostra tre diverse configurazioni di driver basati su DBMS. Nella configurazione del primo, il driver e l'origine dati si trovano nello stesso computer. Nel secondo, il driver e l'origine dati si trovano in computer diversi. Nel terzo, il driver e l'origine dati si trovano in computer diversi e un gateway si trova tra di essi, che si trovano in un altro computer.  
  
 ![Tre configurazioni per DBMS &#45; base driver](../../odbc/reference/media/pr07.gif "pr07")
