---
title: Rinominare viste | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-views
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9577d5597eff0cb2bd3e30771c4e2765eadb42b6
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="rename-views"></a>Rinominare viste
  È possibile rinominare una vista in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  Se si rinomina una vista, è possibile che smettano di funzionare il codice e le applicazioni che dipendono da essa, incluse altre viste, query, stored procedure, funzioni definite dall'utente e applicazioni client. Tali errori inoltre tendono a propagarsi a cascata.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Sicurezza](#Security)  
  
-   **Per rinominare una vista usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a view](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Ottenere un elenco di tutte le dipendenze dalla vista. È necessario modificare qualsiasi oggetto, script o applicazione che fa riferimento alla vista per riflettere il nuovo nome di quest'ultima. Per altre informazioni, vedere [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md). Si consiglia di eliminare la vista e di ricrearla con un nuovo nome anziché rinominarla. Se si ricrea la vista, si aggiornano le informazioni sulle dipendenze per gli oggetti a cui viene fatto riferimento nella vista.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Sono richieste l'autorizzazione ALTER per SCHEMA o CONTROL per OBJECT e l'autorizzazione CREATE VIEW per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>Per rinominare una vista  
  
1.  In **Esplora oggetti**espandere il database contenente la vista da rinominare, quindi espandere la cartella **Vista** .  
  
2.  Fare clic con il pulsante destro del mouse sulla vista da rinominare e scegliere **Rinomina**.  
  
3.  Immettere il nuovo nome della vista.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per rinominare una vista**  
  
 Nonostante sia possibile usare **sp_rename** per modificare il nome della vista, si consiglia di eliminare quella esistente e di ricrearla con il nuovo nome.  
  
 Per altre informazioni, vedere [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md) e [DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md).  
  
##  <a name="FollowUp"></a> Completamento: Dopo la rinomina di una vista  
 Assicurarsi che per tutti gli oggetti, script e applicazioni che fanno riferimento al nome obsoleto della vista venga usato il nuovo nome.  
  
  
