---
title: Categoria di eventi Blocchi| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 03038c96384ffa83a9a2ae773de6d676e9fa48c2
ms.sourcegitcommit: beaad940c348ab22d4b4a279ced3137ad30c658a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="locks-event-category"></a>Categoria di eventi Blocchi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le classi di evento della categoria di eventi **Locks** consentono di monitorare l'attività di blocco in un'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Queste classi di evento possono contribuire a esaminare problemi di blocco provocati dalla lettura e modifica dei dati da parte di più utenti simultaneamente.  
  
 Poiché nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono spesso elaborati più blocchi, l'acquisizione delle classi di evento **Locks** durante una traccia può provocare un overhead significativo e comportare la creazione di file o tabelle di traccia di grandi dimensioni.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento Deadlock Graph](../../relational-databases/event-classes/deadlock-graph-event-class.md)|Include una descrizione XML di un deadlock.|  
|[Classe Lock:Acquired Event](../../relational-databases/event-classes/lock-acquired-event-class.md)|Indica l'acquisizione di un blocco su una risorsa, ad esempio una riga in una tabella.|  
|[Classe di evento Lock:Cancel](../../relational-databases/event-classes/lock-cancel-event-class.md)|Tiene traccia delle richieste di blocchi annullate prima dell'acquisizione del blocco, ad esempio per evitare un deadlock.|  
|[Classe di evento Lock:Deadlock Chain](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)|Esegue il monitoraggio di condizioni di deadlock e degli oggetti coinvolti.|  
|[Classe di evento Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)|Tiene traccia di una richiesta di blocco da parte di una transazione su una risorsa già bloccata da un'altra transazione e del deadlock risultante.|  
|[Classe di evento Lock:Escalation](../../relational-databases/event-classes/lock-escalation-event-class.md)|Indica la conversione di un blocco con granularità fine in un blocco con granularità grossolana.|  
|[Classe di evento Lock:Released](../../relational-databases/event-classes/lock-released-event-class.md)|Tiene traccia del rilascio di un blocco.|  
|[Lock:Timeout &#40;timeout &#62; 0&#41; Event Class](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)|Tiene traccia dell'impossibilità di completare richieste di blocco a causa del blocco della risorsa richiesta da parte di un'altra transazione. Questo evento viene generato solo nei casi in cui il valore specificato per il timeout del blocco è superiore a zero.|  
|[Classe di evento Lock:Timeout](../../relational-databases/event-classes/lock-timeout-event-class.md)|Tiene traccia dell'impossibilità di completare richieste di blocco a causa del blocco della risorsa richiesta da parte di un'altra transazione.|  
  
  
