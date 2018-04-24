---
title: Documentazione per gli sviluppatori di replica | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f3f7bf4a8c6b74a3f4f6e6531594d96173909b9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="replication-developer-documentation"></a>Documentazione per gli sviluppatori di replica
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  La possibilità da configurare, gestire e monitorare a livello di codice una topologia di replica consente di semplificare le attività di replica ripetute e di migliorare l'esperienza utente per le applicazioni basate sulla replica. Mediante la programmazione della replica, è possibile offrire funzionalità di replica personalizzate agli utenti finali, senza che sia necessario conoscere le stored procedure di replica e i file eseguibili degli agenti di replica o utilizzare l'interfaccia di replica implementata da [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 Di seguito vengono descritti gli scenari in cui le applicazioni possono trarre vantaggio dall'accesso a livello di codice ai servizi di replica:  
  
-   Aggiunta di funzionalità di replica a un'applicazione dell'utente finale esistente, ad esempio la sincronizzazione di una sottoscrizione pull quando l'utente fa clic su un pulsante.  
  
-   Creazione di un'interfaccia utente basata sul web per l'amministrazione remota della replica.  
  
-   Creazione di un'interfaccia utente personalizzata che esponga solo un subset delle funzionalità di amministrazione e che possa essere utilizzata per l'amministrazione remota di più topologie di replica da un solo percorso o che combini funzionalità di amministrazione e di sincronizzazione.  
  
-   Miglioramento di uno strumento di monitoraggio esistente mediante l'aggiunta di funzionalità di controllo dello stato di una pubblicazione o di una sottoscrizione o presso il server di distribuzione.  
  
-   Creazione di un'applicazione personalizzata per amministrare o sincronizzare sottoscrizioni di un server di pubblicazione Oracle.  
  
-   Scrittura di regole business personalizzate da eseguire alla sincronizzazione di una sottoscrizione di tipo merge.  
  
-   Generazione di script [!INCLUDE[tsql](../../../includes/tsql-md.md)] che possono essere eseguiti ripetutamente durante la configurazione di nuovi sottoscrittori.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente di controllare a livello di codice gli agenti di replica e di amministrare e monitorare a livello di codice una topologia di replica. Per altre informazioni sulla programmazione della replica, vedere [Concetti di base relativi alla programmazione della replica](../../../relational-databases/replication/concepts/replication-programming-concepts.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Concetti di base relativi alla programmazione della replica](../../../relational-databases/replication/concepts/replication-programming-concepts.md)  
 Descrive i passaggi di pianificazione per lo sviluppo di un'applicazione che utilizza la replica.  
  
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
 Descrive come è possibile utilizzare stored procedure di sistema per fornire l'accesso a livello di codice in una topologia di replica.  
  
 [Concetti di base relativi a RMO (Replication Management Objects)](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
 Illustra i concetti di base per l'utilizzo di RMO (Replication Management Objects), ovvero un assembly di codice gestito che incapsula le funzionalità di replica per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Concetti di base relativi ai file eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
 Descrive l'utilizzo di file eseguibili dell'agente di replica.  
  
 [Guida per gli sviluppatori: Procedure &#40;replica&#41;](../../../relational-databases/replication/concepts/developer-s-guide-how-to-topics-replication.md)  
 Fornisce un elenco di procedure correlate alla replica.  
  
  
