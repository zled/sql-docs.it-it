---
title: Eliminare un proxy di SQL Server Agent | Microsoft Docs
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
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8371f1b086c15881e6cfd125194038d5c8245b72
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="delete-a-sql-server-agent-proxy"></a>Delete a SQL Server Agent Proxy
In questo argomento viene descritto come eliminare un account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per eliminare un account proxy di SQL Server Agent utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   Quando si elimina un account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, assicurarsi che il proxy non faccia riferimento ad alcun passaggio di processo attivo. Per verificare eventuali passaggi di processo che fanno riferimento al proxy, fare clic con il pulsante destro del mouse sul proxy, scegliere **Proprietà**e quindi nella finestra di dialogo *Proprietà account proxy***nome_proxy** selezionare la pagina **Riferimenti** . Se si elimina un proxy, la finestra di dialogo **Elimina oggetto** consente di riassegnare tutti i passaggi di processo che utilizzano tale proxy.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent utilizzano le credenziali per archiviare le informazioni sugli account utente di Windows. L'utente specificato nella credenziale deve disporre dell'autorizzazione "accesso come processo batch" sul computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent verifica l'accesso al sottosistema per un proxy e garantisce l'accesso al proxy ad ogni esecuzione del passaggio di processo. Se il proxy non dispone più di accesso al sottosistema, il passaggio di processo non viene eseguito correttamente. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent rappresenta l'utente specificato nel proxy ed esegue il passaggio di processo.  
  
-   Se l'account di accesso per l'utente viene utilizzato per l'accesso al proxy oppure se l'utente appartiene a un qualsiasi ruolo che prevede l'accesso al proxy, l'utente potrà utilizzare il proxy in un passaggio di processo.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Gli account proxy possono essere creati, modificati o eliminati unicamente dai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Per eliminare un account proxy di SQL Server Agent  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere un server che contiene l'account proxy da eliminare.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Proxy** .  
  
4.  Fare clic sul segno più per espandere il sottosistema che contiene l'account proxy da eliminare, ad esempio **ActiveX Script**.  
  
5.  Fare clic con il pulsante destro del mouse sull'account proxy da eliminare e quindi scegliere **Elimina**.  
  
6.  Nella finestra di dialogo **Elimina oggetto** verificare che sia selezionato l'account proxy corretto. Selezionare la casella di controllo **Riassegna a** per riassegnare i passaggi del processo che si riferiscono all'account proxy a un altro account.  
  
7.  Scegliere **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Per eliminare un account proxy di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_delete_proxy (Transact-SQL)](http://msdn.microsoft.com/en-us/44a1db13-b7f2-4dab-a1b5-b8dafb41737c).  
  

