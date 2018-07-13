---
title: Completare i passaggi di post-installazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 21f2b02a1e3f030fda9cbdc29d85bbfe8a3dd508
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181048"
---
# <a name="complete-the-post-installation-steps"></a>Completare i passaggi successivi all'installazione
  Dopo aver installato il componente Riesecuzione distribuita, è necessario modificare gli account del controller e del servizio client relativi.  
  
### <a name="to-complete-the-post-installation-steps"></a>Per completare i passaggi di post-installazione  
  
1.  **Creare regole del firewall**: nei computer controller e client è necessario consentire il traffico in ingresso attraverso il firewall per il servizio corrispondente. Specificare le regole del firewall per i file eseguibili del servizio, all'interno delle cartelle di installazione.  
  
    1.  Per il servizio controller, creare una regola per **DReplayController.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Per il servizio client, in ogni computer client creare una regola per **DReplayClient.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Concedere a ogni client le autorizzazioni per il server di destinazione**: al termine dell'installazione del servizio client nei computer client, è necessario aggiungere manualmente gli account del servizio client al ruolo sysadmin nell'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Per installare qualsiasi funzionalità di Riesecuzione distribuita, è necessario disporre di autorizzazioni di amministratore. Solo un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che dispone di autorizzazioni sysadmin può aggiungere gli account del servizio client al ruolo del server sysadmin del server di prova. Per alcune considerazioni relative alla sicurezza di Riesecuzione distribuita, vedere [Distributed Replay Security](distributed-replay-security.md).  
  
  
