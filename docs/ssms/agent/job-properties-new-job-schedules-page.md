---
title: Proprietà processo - Nuovo processo (pagina Pianificazioni) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e97c52943b2f6d6092c40d121ee88ea8d6b814c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33039838"
---
# <a name="job-properties---new-job-schedules-page"></a>Proprietà processo - Nuovo processo (pagina Pianificazioni)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Usare questa pagina per visualizzare e organizzare le pianificazioni relative a un processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Elenco pianificazioni**  
Elenca le pianificazioni relative al processo corrente.  
  
**Nuova**  
Consente di creare una nuova pianificazione. Dopo la creazione, la pianificazione verrà aggiunta al processo.  
  
**Seleziona**  
Consente di selezionare una pianificazione tra quelle esistenti. Poiché un processo e una pianificazione devono avere lo stesso proprietario, questa opzione consente soltanto di selezionare una pianificazione dall'elenco di quelle di cui si è proprietari.  
  
**Modifica**  
Consente di modificare la pianificazione selezionata per cambiare le proprietà di pianificazione di un processo.  
  
**Rimuovi**  
Consente di rimuovere dal processo la pianificazione selezionata. Se la pianificazione non è utilizzata da altri processi, viene eliminata dal database.  
  
## <a name="see-also"></a>Vedere anche  
[Implementazione di processi](../../ssms/agent/implement-jobs.md)  
  
