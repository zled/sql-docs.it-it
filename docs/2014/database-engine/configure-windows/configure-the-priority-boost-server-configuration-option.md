---
title: Configurare l'opzione di configurazione del server priority boost | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- priority boost option
ms.assetid: 765f1e83-dd52-44fb-b0c8-1078f213607b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bad83198d31fb2733e0bcc15c5a6a2d19a2b9189
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224491"
---
# <a name="configure-the-priority-boost-server-configuration-option"></a>Configurare l'opzione di configurazione del server priority boost
  In questo argomento si illustra come configurare l'opzione di configurazione del server **priority boost** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilizzare l'opzione **priority boost** per specificare se [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere eseguito con una priorità di pianificazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 o Windows 2008 R2 superiore a quella di altri processi nello stesso computer. Se l'opzione viene impostata su 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito con un valore base di priorità pari a 13 nell'utilità di pianificazione di Windows 2008 o Windows 2008 R2. L'impostazione predefinita è 0, che corrisponde a un valore base di priorità pari a 7.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per configurare l'opzione priority boost utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la configurazione dell'opzione priority boost](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   L'aumento eccessivo della priorità può sottrarre risorse a funzionalità di sistema e di rete essenziali, provocando problemi nell'arresto di SQL Server o nell'utilizzo di altre attività dei sistemi operativi nel server.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Le autorizzazioni di esecuzione per **sp_configure** senza alcun parametro o solo con il primo parametro vengono assegnate per impostazione predefinita a tutti gli utenti. Per eseguire **sp_configure** con entrambi i parametri per la modifica di un'opzione di configurazione o per l'esecuzione dell'istruzione RECONFIGURE, a un utente deve essere concessa l'autorizzazione a livello di server ALTER SETTINGS. L'autorizzazione ALTER SETTINGS è assegnata implicitamente ai ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-the-priority-boost-option"></a>Per configurare l'opzione priority boost  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un server e scegliere **Proprietà**.  
  
2.  Fare clic sul nodo **Processori** .  
  
3.  In **Thread**selezionare la casella di controllo **Aumenta priorità di SQL Server** .  
  
4.  Arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-configure-the-priority-boost-option"></a>Per configurare l'opzione priority boost  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Questo esempio illustra come usare [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) per impostare il valore dell'opzione `priority boost` su `1`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'priority boost', 1 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)sia installato il servizio WMI.  
  
##  <a name="FollowUp"></a> Completamento: Dopo la configurazione dell'opzione priority boost  
 Per poter rendere effettiva l'impostazione, è necessario riavviare il server.  
  
## <a name="see-also"></a>Vedere anche  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
