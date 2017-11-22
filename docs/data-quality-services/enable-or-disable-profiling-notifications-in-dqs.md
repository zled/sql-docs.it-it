---
title: Abilitare o disabilitare le notifiche di profiling in DQS | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: data-quality-services
ms.reviewer: 
ms.suite: sql
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce6dede35f7f602999f74e00ff48e34622fde26c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a>Abilitare o disabilitare le notifiche di profiling in DQS
  In questo argomento viene descritto come abilitare o disabilitare le notifiche di profiling in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Per impostazione predefinita, le notifiche di profiling in DQS sono abilitate. Le notifiche di profiling forniscono informazioni importanti sull'origine dati e sull'efficacia dell'attività corrente in esecuzione sui dati. Per altre informazioni, vedere [Data Profiling and Notifications in DQS](../data-quality-services/data-profiling-and-notifications-in-dqs.md).  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per abilitare le notifiche, è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Enable"></a> Abilitare o disabilitare le notifiche di profiling  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Configurazione**.  
  
3.  Fare clic sulla scheda **Impostazioni generali** .  
  
4.  Deselezionare o selezionare la casella di controllo **Abilita notifiche** per disabilitare o abilitare le notifiche di profiling per le varie attività in DQS.  
  
5.  Scegliere **Chiudi**.  
  
  
