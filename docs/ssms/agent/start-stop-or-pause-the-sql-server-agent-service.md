---
title: Avviare, arrestare o sospendere il servizio SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: af137c019a7f96769b801d01f882e1d98b0da2ea
ms.contentlocale: it-it
ms.lasthandoff: 08/18/2017

---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Avvio, arresto o sospensione del servizio SQL Server Agent
In questo argomento viene illustrato come avviare, arrestare o riavviare il servizio SQL Server Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
È possibile configurare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per l'avvio automatico all'avvio del sistema operativo oppure è possibile avviarlo manualmente quando è necessario completare processi. È possibile arrestare o sospendere il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per sospendere processi, notifiche agli operatori e avvisi.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   [Per avviare, arrestare o riavviare il servizio SQL Server Agent utilizzando SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent venga eseguito come servizio. Per altre informazioni, vedere [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
-   In Esplora oggetti viene visualizzato il nodo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent solo se si dispone dell'autorizzazione per utilizzarlo.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Per la corretta esecuzione delle funzioni, è necessario che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent sia configurato per utilizzare le credenziali di un account membro del ruolo predefinito del server **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. L'account deve disporre delle autorizzazioni di Windows seguenti:  
  
-   Accesso come servizio (SeServiceLogonRight)  
  
-   Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)  
  
-   Ignorare controllo incrociato (SeChangeNotifyPrivilege)  
  
-   Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)  
  
Per altre informazioni sulle autorizzazioni di Windows necessarie per l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere [Selezionare un account per il servizio SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) e [Impostazione di account di servizio Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Per avviare, arrestare o riavviare il servizio SQL Server Agent  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera gestire il servizio SQL Server Agent.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi selezionare **Avvia**, **Arresta**o **Riavvia**.  
  
3.  Nella finestra di dialogo **Controllo account utente** fare clic su **Sì**.  
  
4.  Se viene richiesto di eseguire l'azione, fare clic su **Sì**.  
  
Per altre informazioni, vedere:  
  
-   [Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](http://msdn.microsoft.com/en-us/32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [Avvio automatico di SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/autostart-sql-server-agent-sql-server-management-studio.md)  
  

