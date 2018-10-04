---
title: Connettività client Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53f514e83e980e0a91184581d186bcb4046727c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192747"
---
# <a name="always-on-client-connectivity-sql-server"></a>Connettività client Always On (SQL Server)
  In questo argomento vengono illustrate le considerazioni relative alla connettività client ai gruppi di disponibilità AlwaysOn, inclusi prerequisiti, restrizioni e indicazioni per configurazioni e impostazioni client.  
  
 
  
##  <a name="ClientConnSupport"></a> Supporto della connettività client  
 Nella sezione riportata di seguito vengono fornite informazioni sul supporto di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] per la connettività client.  
  
 **Supporto driver**  
  
 Nella tabella seguente viene riepilogato il supporto di driver per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:  
  
|Driver|Failover su più subnet|Finalità dell'applicazione|Routing di sola lettura|Failover su più subnet: failover dell'endpoint su una sola subnet più rapido|Failover su più subnet: risoluzione dell'istanza denominata per le istanze cluster di SQL|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Sì|Sì|Sì|Sì|Sì|  
|SQL Native Client 11.0 OLEDB|no|Sì|Sì|no|no|  
|ADO.NET con .NET Framework 4.0 con patch di connettività**<sup>*</sup>**|Sì|Sì|Sì|Sì|Sì|  
|ADO.NET con.NET Framework 3.5 SP1 con patch di connettività **<sup>**</sup>**|Sì|Sì|Sì|Sì|Sì|  
|Microsoft JDBC Driver 4.0 per SQL Server|Sì|Sì|Sì|Sì|Sì|  
  
 **<sup>*</sup>**  Scaricare la patch di connettività per ADO .NET con .NET Framework 4.0: [ http://support.microsoft.com/kb/2600211 ](http://support.microsoft.com/kb/2600211).  
  
 **<sup>**</sup>* * Scaricare la patch di connettività per ADO.NET con .NET Framework 3.5 SP1: [ http://support.microsoft.com/kb/2654347 ](http://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  Per connettersi a un listener del gruppo di disponibilità, un client deve utilizzare una stringa di connessione TCP.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creazione e configurazione di gruppi di disponibilità &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Clustering di failover e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Informazioni sull'accesso alla connessione client per le repliche di disponibilità &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server AlwaysOn Team Blog: Il Blog ufficiale di SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)   
 [Si verifica un ritardo prolungato quando si riconnette una connessione IPsec da un computer in cui è in esecuzione Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 o Windows Server 2008 R2](http://support.microsoft.com/kb/980915)   
 [Il servizio cluster impiega circa 30 secondi per il failover su indirizzi IP IPv6 in Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)   
 [Failover lento se non esiste alcun router tra il cluster e un server applicazioni](http://support.microsoft.com/kb/2582281)  
  
  
