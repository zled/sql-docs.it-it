---
title: Visualizzare informazioni su un avviso | Microsoft Docs
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
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5bfe05dde95b8fdb47893ea17802b0798de9762a
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="view-information-about-an-alert"></a>View Information About an Alert
In questo argomento viene descritto come visualizzare le infomazioni sugli avvisi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per visualizzare informazioni su un avviso utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Per impostazione predefinita, i membri del ruolo predefinito del server **sysadmin** possono visualizzare le informazioni su un avviso. Gli altri utenti devono appartenere al ruolo predefinito del database **SQLAgentOperatorRole** nel database **msdb** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>Per visualizzare informazioni su un avviso  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server in cui si desidera visualizzare le informazioni su un avviso.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Avvisi** .  
  
4.  Fare clic con il pulsante destro del mouse sull'avviso con le informazioni da visualizzare e selezionare **Proprietà**.  
  
    Per altre informazioni sulle opzioni disponibili contenute nella finestra di dialogo dell'interfaccia utente nella finestra di dialogo *Proprietà dell'avviso***nome_avviso** , vedere:  
  
    -   [Proprietà avviso - nuovo avviso &amp;#40; pagina generale&amp;#41;](../../ssms/agent/alert-properties-new-alert-general-page.md)  
  
    -   [Proprietà avviso - nuovo avviso &amp;#40; pagina risposta&amp;#41;](../../ssms/agent/alert-properties-new-alert-response-page.md)  
  
    -   [Proprietà avviso - nuovo avviso &amp;#40; pagina Opzioni&amp;#41;](../../ssms/agent/alert-properties-new-alert-options-page.md)  
  
    -   [Proprietà avviso &amp;#40;pagina Cronologia&amp;#41;](../../ssms/agent/alert-properties-history-page.md)  
  
5.  Al termine, fare clic su **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>Per visualizzare informazioni su un avviso  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_help_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/850cef4e-6348-4439-8e79-fd1bca712091).  
  

