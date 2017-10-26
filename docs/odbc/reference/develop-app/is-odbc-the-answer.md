---
title: "La risposta è ODBC? | Microsoft Docs"
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
- interoperability [ODBC], ODBC
ms.assetid: bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2ada446a96ecb6fd81d05380c8a29707eb41f8ee
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="is-odbc-the-answer"></a>La risposta è ODBC?
Prima di affrontare il problema di interoperabilità, prendere in considerazione i seguenti aspetti: l'applicazione utilizzare ODBC affatto? Ciò potrebbe sembrare una domanda strano per porre in una Guida per ODBC, ma è, in realtà, una legittima. ODBC non è stato progettato per sostituire completamente l'API di database native, né è stato progettato per fornire l'accesso al database in tutte le circostanze. È stato progettato per fornire un'interfaccia comune per i database e può essere disponibile ai programmatori di dover conoscere e gestire i collegamenti a più database.  
  
 Applicazioni personalizzate sono candidati ideali per l'API nativa sul database. Il motivo principale è che le applicazioni personalizzate spesso lavorare con un singolo DBMS e non sono necessari per l'interoperabilità. Database nativo API potrebbero presentano le prestazioni migliori rispetto a ODBC di esporre le funzionalità di un determinato DBMS e potrebbero esporre funzionalità non esposta da ODBC. Inoltre, poiché gli sviluppatori di applicazioni personalizzate sono in genere familiari con l'API di database nativo per il sistema DBMS, è necessario informazioni ODBC. Tuttavia, è interessante notare che per alcuni DBMS, ODBC è l'API nativa sul database.  
  
 Pertanto, quali applicazioni sono candidati per ODBC? I migliori candidati sono applicazioni che funzionano con più di un sistema DBMS. Questo include quasi tutte le applicazioni verticali e non generici. Include inoltre un numero di applicazioni personalizzate. Ad esempio, applicazioni personalizzate che utilizzano diversi DBMS diversi sono molto più semplice e più chiara per scrivere con ODBC rispetto con più API native. E applicazioni personalizzate scritte con ODBC sono molto più semplice eseguire la migrazione di una società si sposta da un DBMS a un altro o distribuisce la stessa applicazione su diversi DBMS.

