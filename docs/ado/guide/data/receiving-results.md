---
title: Ricezione dei risultati | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f44ce33a920cecb68a23143d0909072076b44626
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="receiving-results"></a>Ricezione dei risultati
In ADO la maggior parte dei comandi generare alcune informazioni restituite al chiamante. Per la restituzione di set di righe di comandi, i risultati vengono ricevuti un **Recordset** oggetto, è probabile che gli oggetti ADO più utilizzato.  
  
 Esistono diversi modi di ricevere i dati in un **Recordset** oggetto da un'origine dati, tra cui la chiamata seguente:  
  
-   [Connection. Execute (metodo)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command. Execute (metodo)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Open (metodo)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Ricezione di dati in un **Recordset** oggetto conclude il processo di recupero di dati, con la partecipazione di un **connessione** oggetto e un **comando** dell'oggetto, in modo implicito o in modo esplicito. In un sistema di applicazioni client/server tipico, l'intero processo di recupero di dati richiede un round trip in rete per ogni compilato **Recordset**.  
  
 Per ricevere più di un set di risultati significa che è necessario rendere più round trip in rete, uno per ogni set di dati incapsulate in un **Recordset** oggetto. Per le reti lente o sovraccarica, riducendo il numero di round trip può contribuire a migliorare le prestazioni dell'applicazione. Di conseguenza, alcuni provider offrono supporto per la ricezione di più **Recordset**s in un unico round trip. Questo aspetto è illustrato nel seguente argomento:  
  
-   [Ricezione di più recordset](../../../ado/guide/data/receiving-multiple-recordsets.md)
