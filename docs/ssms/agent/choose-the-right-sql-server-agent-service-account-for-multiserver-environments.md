---
title: Scegliere l'account del servizio SQL Server Agent per ambienti multiserver | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d9ccc867f1b4e54ef3d304277a5b0ad6725765c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Scegliere l'account di servizio SQL Server Agent adatto ad ambienti multiserver
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L'account di Windows scelto per il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent può influenzare il comportamento di un ambiente multiserver, come illustrato di seguito:  
  
-   Se si esegue il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent con un account che non appartiene al gruppo Administrators locale di Windows, è possibile che l'integrazione dei server di destinazione nei server master abbia esito negativo. In questo caso, verrà visualizzato il messaggio di errore seguente:  
  
    "Operazione di integrazione non riuscita."  
  
    Per risolvere il problema, riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
-   Quando il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent viene eseguito con l'account di sistema locale, le operazioni tra server master e server di destinazione sono supportate solo se entrambi risiedono nello stesso computer. Se si utilizza questa configurazione, quando si integrano i server di destinazione in un server master, verrà visualizzato il seguente messaggio:  
  
    "Verifica che l'account di avvio dell'agente per *<nome_computer_server_destinazione>* disponga dei diritti per l'accesso come server di destinazione".  
  
    Questo messaggio può essere ignorato. L'operazione di integrazione verrà completata correttamente.  
  
Per informazioni su come selezionare l'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere [Selezionare un account per il servizio SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
