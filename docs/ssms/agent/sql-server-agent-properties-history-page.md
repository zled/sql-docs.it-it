---
title: Proprietà SQL Server Agent (pagina Cronologia) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 92c8938b332ec2b4ad8a1b9dd99c4ce8e420bfe2
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-agent-properties-history-page"></a>Proprietà SQL Server Agent (pagina Cronologia)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Usare questa pagina per visualizzare e modificare le impostazioni di gestione del log della cronologia del servizio di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Limita dimensioni log cronologia processo**  
Consente di impostare limiti sulla quantità di informazioni sulla cronologia processo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene nel log.  
  
**Dimensioni massime log cronologia processo (righe)**  
Consente di impostare il numero massimo di righe che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene nel log. Quando il log raggiunge dimensioni tali da contenere questo numero di righe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent rimuove le righe meno recenti per consentire l'inserimento delle nuove.  
  
**Numero massimo di righe di cronologia per processo**  
Consente di impostare il numero massimo di righe che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene per ogni processo. Quando la cronologia di un determinato processo si estende fino a contenere questo numero di righe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent consente di rimuovere le righe meno recenti per consentire l'inserimento delle nuove.  
  
**Rimuovi cronologia dell'agente**  
Viene indicato che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent consentirà di rimuovere le voci presenti nel log da più tempo rispetto a quanto specificato. Si tratta di un'esecuzione singola che consente di rimuovere la cronologia. Se è necessario un processo ricorrente, creare e pianificare un piano di manutenzione con un processo di pulizia.  
  
**Più vecchia di**  
Consente di impostare il periodo di tempo per cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent manterrà le voci.  
  
## <a name="see-also"></a>Vedere anche  
[Log degli errori di SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)  
  
