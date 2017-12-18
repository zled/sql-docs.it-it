---
title: 'Lezione 1: Creazione di account di Windows per la replica | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9688b2bac34a38ea667557b997adfed3e7cf37d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Lezione 1: Creazione di account di Windows per la replica
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] In questa lezione verranno creati account di Windows per l'esecuzione degli agenti di replica. Verrà creato un account di Windows separato nel server locale per gli agenti seguenti:  
  
|Agente|Percorso|Nome account|  
|---------|------------|----------------|  
|agente snapshot|Server di pubblicazione|\<*nome_computer*>\repl_snapshot|  
|Agente di lettura log|Server di pubblicazione|\<*nome_computer*>\repl_logreader|  
|Agente di distribuzione|Server di pubblicazione e Sottoscrittore|\<*nome_computer*>\repl_distribution|  
|Agente di merge|Server di pubblicazione e Sottoscrittore|\<*nome_computer*>\repl_merge|  
  
> [!NOTE]  
> Nelle esercitazioni sulla replica i server di pubblicazione e il server di distribuzione condividono la stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il server di pubblicazione e il Sottoscrittore possono utilizzare la stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma ciò non è un requisito. Se il server di pubblicazione e il Sottoscrittore condividono la stessa istanza, i passaggi utilizzati per creare gli account del Sottoscrittore non sono obbligatori.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Per creare account di Windows locali per gli agenti di replica nel server di pubblicazione  
  
1.  Nel server di pubblicazione fare clic su **Gestione computer** in **Strumenti di amministrazione** nel Pannello di controllo.  
  
2.  In **Utilità di sistema**espandere **Utenti e gruppi locali**.  
  
3.  Fare clic con il pulsante destro del mouse su **Utenti** e scegliere **Nuovo utente**.  
  
4.  Immettere **repl_snapshot** nella casella **Nome utente** , specificare la password e altre informazioni importanti e fare clic su **Crea** per creare l'account repl_snapshot.  
  
5.  Ripetere il passaggio precedente per creare gli account repl_logreader, repl_distribution e repl_merge.  
  
6.  Scegliere **Chiudi**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Per creare account di Windows locali per gli agenti di replica nel Sottoscrittore  
  
1.  Nel Sottoscrittore fare clic su **Gestione computer** in **Strumenti di amministrazione** nel Pannello di controllo.  
  
2.  In **Utilità di sistema**espandere **Utenti e gruppi locali**.  
  
3.  Fare clic con il pulsante destro del mouse su **Utenti** e scegliere **Nuovo utente**.  
  
4.  Immettere **repl_distribution** nella casella **Nome utente** , specificare la password e altre informazioni importanti e fare clic su **Crea** per creare l'account repl_distribution.  
  
5.  Ripetere il passaggio precedente per creare l'account repl_merge.  
  
6.  Scegliere **Chiudi**.  
  
## <a name="next-steps"></a>Passaggi successivi  
In questo modo sono stati creati gli account di Windows per gli agenti di replica. Il passaggio successivo consiste nella configurazione della cartella snapshot. Vedere [Lezione 2: Preparazione della cartella snapshot](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
  
