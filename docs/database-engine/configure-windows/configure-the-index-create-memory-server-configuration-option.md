---
title: Configurare l'opzione di configurazione del server index create memory | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2bb4dddd24def2a1e442b7dded3b1054729b587f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a>Configurare l'opzione di configurazione del server index create memory
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In questo argomento si illustra come configurare l'opzione di configurazione del server **index create memory** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Con l'opzione **index create memory** è possibile controllare la quantità massima di memoria allocata inizialmente per la creazione di indici. Il valore predefinito per questa opzione è 0 (configurazione automatica). Se in un secondo momento risulta necessaria una quantità maggiore di memoria per la creazione degli indici e la memoria è disponibile, verrà usata dal server, superando quindi le impostazioni relative a questa opzione. Se non è disponibile ulteriore memoria, la creazione degli indici continuerà, usando la memoria già allocata.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per configurare l'opzione index create memory tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la configurazione dell'opzione index create memory](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   L'impostazione dell'opzione **min memory per query** ha la precedenza sull'opzione **index create memory** . Se si modificano entrambe le opzioni e **index create memory** è minore di **min memory per query**, verrà visualizzato un messaggio di avviso, ma il valore risulterà impostato. Durante l'esecuzione della query verrà visualizzato un avviso analogo.  
  
-   Quando si usano tabelle e indici partizionati, è possibile che i requisiti minimi di memoria aumentino in modo significativo in caso di indici partizionati non allineati e di un grado elevato di parallelismo. Con questa opzione è possibile controllare la quantità totale iniziale di memoria allocata per tutte le partizioni dell'indice in un'unica operazione di creazione dell'indice. Se la quantità impostata tramite questa opzione è inferiore rispetto al valore minimo necessario per l'esecuzione, la query verrà terminata e verrà visualizzato un messaggio di errore.  
  
-   Il valore di esecuzione per questa opzione non supererà la quantità di memoria effettiva che può essere usata per il sistema operativo e la piattaforma hardware in cui viene eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Questa opzione è avanzata e la relativa modifica è riservata ad amministratori di database esperti o a tecnici dotati di certificazione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Index Create Memory** è un'opzione a configurazione automatica e solitamente non richiede alcuna modifica. Se tuttavia si riscontrano difficoltà nella creazione di indici, valutare l'opportunità di aumentare il valore dell'opzione.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Le autorizzazioni di esecuzione per **sp_configure** senza alcun parametro o solo con il primo parametro vengono assegnate per impostazione predefinita a tutti gli utenti. Per eseguire **sp_configure** con entrambi i parametri per la modifica di un'opzione di configurazione o per l'esecuzione dell'istruzione RECONFIGURE, a un utente deve essere concessa l'autorizzazione a livello di server ALTER SETTINGS. L'autorizzazione ALTER SETTINGS è assegnata implicitamente ai ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Per configurare l'opzione index create memory  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un server e scegliere **Proprietà**.  
  
2.  Fare clic sul nodo **Memoria** .  
  
3.  In **Memoria per la creazione degli indici**digitare o selezionare il valore desiderato per l'opzione index create memory.  
  
     L'opzione **index create memory** consente di gestire la quantità di memoria usata dagli ordinamenti per la creazione di indici. **index create memory** è un'opzione a configurazione automatica e nella maggior parte può essere usata senza apportare alcuna modifica. Se tuttavia si riscontrano difficoltà nella creazione di indici, valutare l'opportunità di aumentare il valore dell'opzione. Gli ordinamenti per le query sono gestiti tramite l'opzione **min memory per query** .  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Per configurare l'opzione index create memory  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Questo esempio illustra come usare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) per impostare il valore dell'opzione `index create memory` su `4096`.  
  
```tsql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Completamento: Dopo la configurazione dell'opzione index create memory  
 L'impostazione diventa effettiva immediatamente senza dover riavviare il server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opzioni di configurazione del server Server Memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
