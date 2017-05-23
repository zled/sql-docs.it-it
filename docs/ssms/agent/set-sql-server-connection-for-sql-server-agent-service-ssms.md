---
title: Impostare la connessione a SQL Server per il servizio SQL Server Agent | Microsoft Docs
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
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4129f5324f4b93efb98e9bd437571daa0bc404a1
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
In questo argomento viene illustrato come impostare la connessione tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e [!INCLUDE[ssDE](../../includes/ssde_md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Per la connessione a un'istanza locale di SQL Server il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent può utilizzare Autenticazione di Windows.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per impostare Connessione SQL Server per SQL Server Agent tramite:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   In Esplora oggetti viene visualizzato il nodo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent solo se si dispone dell'autorizzazione per utilizzarlo.  
  
-   A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non è supportata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Questa opzione è disponibile solo quando si amministra una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Per la corretta esecuzione delle funzioni, è necessario che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent sia configurato per utilizzare le credenziali di un account membro del ruolo predefinito del server **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. L'account deve disporre delle autorizzazioni di Windows seguenti:  
  
-   Accesso come servizio (SeServiceLogonRight)  
  
-   Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)  
  
-   Ignorare controllo incrociato (SeChangeNotifyPrivilege)  
  
-   Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)  
  
Per altre informazioni sulle autorizzazioni di Windows necessarie per l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere [Selezionare un account per il servizio SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) e [Impostazione di account di servizio Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>Per impostare la connessione a SQL Server  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server che si desidera impostare con una connessione al servizio SQL Server Agent.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent** e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà SQL Server Agent***nome_server* fare clic su **Connessione**in **Seleziona una pagina**.  
  
4.  In **Connessione SQL Server**selezionare **Usa autenticazione di Windows** per abilitare la connessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent a un'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssDE](../../includes/ssde_md.md)] con l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows. Per le connessioni ai database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] e versioni successive è necessario utilizzare l'autenticazione di Windows.  
  

