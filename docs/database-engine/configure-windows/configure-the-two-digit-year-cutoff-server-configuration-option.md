---
title: "Configurare l&#39;opzione di configurazione del server two-digit year cutoff | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "two digit year cutoff - opzione"
  - "anni in formato a quattro cifre [SQL Server]"
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Configurare l&#39;opzione di configurazione del server two-digit year cutoff
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In questo argomento si illustra come configurare l'opzione di configurazione del server **two digit year cutoff** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Con l'opzione **two digit year cutoff** è possibile specificare un intero compreso tra 1753 e 9999 che rappresenta l'anno di cambio data per l'interpretazione degli anni a due cifre come anni a quattro cifre. Il periodo di tempo predefinito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è 1950-2049, dove 2049 rappresenta l'anno di cambio data. Questo significa che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'anno a due cifre 49 viene interpretato come 2049, l'anno a due cifre 50 viene interpretato come 1950 e l'anno a due cifre 99 viene interpretato come 1999. Per compatibilità con versioni precedenti è consigliabile mantenere il valore predefinito.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per configurare l'opzione two digit year cutoff utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la configurazione dell'opzione two digit year cutoff](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Questa opzione è avanzata e la relativa modifica è riservata ad amministratori di database esperti o a tecnici dotati di certificazione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Negli oggetti di automazione OLE viene utilizzato 2030 come anno di cambio data a due cifre. È possibile utilizzare l'opzione **two digit year cutoff** per fornire coerenza nei valori delle date tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e applicazioni client. Per evitare ambiguità nell'utilizzo delle date è consigliabile utilizzare anni a quattro cifre nei dati.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Le autorizzazioni di esecuzione per **sp_configure** senza alcun parametro o solo con il primo parametro vengono assegnate per impostazione predefinita a tutti gli utenti. Per eseguire **sp_configure** con entrambi i parametri per la modifica di un'opzione di configurazione o l'esecuzione dell'istruzione RECONFIGURE, è necessario concedere all'utente l'autorizzazione a livello di server ALTER SETTINGS. L'autorizzazione ALTER SETTINGS è assegnata implicitamente ai ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per configurare l'opzione two digit year cutoff  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un server e scegliere **Proprietà**.  
  
2.  Fare clic sul nodo **Impostazioni varie** .  
  
3.  Nella casella **Interpreta l'immissione di un anno a due cifre come un anno tra**in **Supporto anni a due cifre** **digitare o selezionare il valore desiderato per l'anno** che deve concludere il periodo di tempo desiderato.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per configurare l'opzione two digit year cutoff  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Questo esempio illustra come usare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) per impostare il valore dell'opzione `two digit year cutoff` su `2030`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Completamento: Dopo la configurazione dell'opzione two digit year cutoff  
 L'impostazione diventa effettiva immediatamente senza dover riavviare il server.  
  
## Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  