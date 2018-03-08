---
title: Integrare un server di destinazione in un server master | Microsoft Docs
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
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9659a0e1559138f03452fee96523c42842c11776
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Integrare un server di destinazione in un server master
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come aggiungere server di destinazione a una configurazione di amministrazione multiserver. Eseguire questa procedura dal server master. In [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]o SQL Server Management Objects (SMO).  
  
Per informazioni sugli effetti dell'uso dell'account di Windows per il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent su un ambiente multiserver, vedere [Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md).  
  
Per impostazione predefinita, per le connessioni tra server master e server di destinazione sono attive la crittografia SSL (Secure Sockets Layer) completa e la convalida del certificato. Per altre informazioni, vedere [Impostazione delle opzioni di crittografia nei server di destinazione](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
**Contenuto dell'argomento**  
  
-   **Per integrare un server di destinazione tramite:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>Per integrare un server di destinazione  
  
1.  In **Esplora oggetti**espandere un server configurato come server master.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Amministrazione multiserver**e fare clic su **Aggiungi server di destinazione**.  
  
3.  In Configurazione guidata server di destinazione, eseguire i passaggi necessari per completare la procedura.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>Per integrare un server di destinazione  
  
1.  Usare la stored procedure **sp_msx_enlist** .  Per altre informazioni, vedere [sp_msx_enlist (Transact-SQL)](http://msdn.microsoft.com/en-us/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)  
  
## <a name="see-also"></a>Vedere anche  
[Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
