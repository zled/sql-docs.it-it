---
title: Completare i passaggi di post-installazione | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 375f63cb25259ca3bfcc966d6b41809ad1fa992b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="complete-the-post-installation-steps"></a>Completare i passaggi successivi all'installazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Dopo aver installato Distributed Replay è necessario modificare gli account di servizi client e il controller di riesecuzione distribuita.  
  
### <a name="to-complete-the-post-installation-steps"></a>Per completare i passaggi di post-installazione  
  
1.  **Creare regole del firewall**: nei computer controller e client è necessario consentire il traffico in ingresso attraverso il firewall per il servizio corrispondente. Specificare le regole del firewall per i file eseguibili del servizio, all'interno delle cartelle di installazione.  
  
    1.  Per il servizio controller, creare una regola per **DReplayController.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Per il servizio client, in ogni computer client creare una regola per **DReplayClient.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Concedere a ogni client le autorizzazioni per il server di destinazione**: al termine dell'installazione del servizio client nei computer client, è necessario aggiungere manualmente gli account del servizio client al ruolo sysadmin nell'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Per installare qualsiasi funzionalità di Riesecuzione distribuita, è necessario disporre di autorizzazioni di amministratore. Solo un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che dispone di autorizzazioni sysadmin può aggiungere gli account del servizio client al ruolo del server sysadmin del server di prova. Per alcune considerazioni relative alla sicurezza di Riesecuzione distribuita, vedere [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  
