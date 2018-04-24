---
title: Ottimizzare l'amministrazione automatizzata in un'organizzazione | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 24ae20b48409b95dadf758722e6694d55cf9945f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Ottimizzazione dell'amministrazione automatizzata in un'organizzazione
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

L'amministrazione multiserver implementata da Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent sfrutta le caratteristiche di ottimizzazione automatica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. In condizioni normali, non è pertanto necessario eseguire ottimizzazioni dei processi aggiuntive. L'esecuzione di processi, la generazione di avvisi e le notifiche agli operatori possono tuttavia determinare un aumento dei carichi di rete e in questi casi è possibile ottimizzare l'amministrazione automatizzata all'interno di un'organizzazione in modo da ridurre al minimo il traffico di rete provocato da queste attività.  
  
## <a name="see-also"></a>Vedere anche  
[Monitoraggio delle prestazioni del motore del flusso di dati](http://msdn.microsoft.com/en-us/11e17f4e-72ed-44d7-a71d-a68937a78e4c)  
  
