---
title: "Istruzioni Transact-SQL per i gruppi di disponibilità AlwaysOn | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
caps.latest.revision: "23"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6afc6c135135d53230d8ddcc9aae846e7d21a92
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="transact-sql-statements-for-always-on-availability-groups"></a>Istruzioni Transact-SQL per i gruppi di disponibilità AlwaysOn
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In questo argomento si introducono le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] che supportano la distribuzione di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , nonché la creazione e la gestione di qualsiasi gruppo, replica e database di disponibilità.  
  
 **Contenuto dell'argomento:**  
  
-   [CREATE ENDPOINT](#CreateEndpoint)  
  
-   [CREATE AVAILABILITY GROUP](#CreateAG)  
  
-   [ALTER AVAILABILITY GROUP](#AlterAG)  
  
-   [Opzioni ALTER DATABASE SET HADR](#AlterDb)  
  
-   [DROP AVAILABILITY GROUP](#DropAG)  
  
-   [Restrizioni sulle istruzioni AVAILABILITY GROUP di Transact-SQL](#Restrictions)  
  
##  <a name="CreateEndpoint"></a> CREATE ENDPOINT  
 [CREATE ENDPOINT … FOR DATABASE_MIRRORING](../../../t-sql/statements/create-endpoint-transact-sql.md) consente di creare un endpoint del mirroring di database, se non ne esiste uno nell'istanza del server. Per ogni istanza del server in cui si intende distribuire [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] o il mirroring del database è necessario un endpoint di mirroring del database.  
  
 Eseguire questa istruzione sull'istanza del server nella quale si crea l'endpoint. È possibile creare solo un endpoint del mirroring del database in una determinata istanza del server. Per altre informazioni, vedere [Endpoint del mirroring del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
##  <a name="CreateAG"></a> CREATE AVAILABILITY GROUP  
 Con[CREATE AVAILABILITY GROUP](../../../t-sql/statements/create-availability-group-transact-sql.md) è possibile creare un nuovo gruppo di disponibilità e, facoltativamente, un listener del gruppo di disponibilità. È necessario specificare almeno l'istanza del server locale, che diventerà la replica primaria iniziale. È eventualmente possibile specificare anche un massimo di quattro repliche secondarie.  
  
 Eseguire CREATE AVAILABILITY GROUP nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui si desidera ospitare la replica primaria iniziale del nuovo gruppo di disponibilità. Questa istanza del server deve trovarsi in un nodo di un cluster WSFC (Windows Server Failover Cluster). Per altre informazioni, vedere [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn &#40; SQL Server &#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="AlterAG"></a> ALTER AVAILABILITY GROUP  
 [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) supporta la modifica di un gruppo di disponibilità o di un listener del gruppo di disponibilità esistente, nonché l'esecuzione del failover di un gruppo di disponibilità.  
  
 Eseguire ALTER AVAILABILITY GROUP nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui è ospitata la replica primaria iniziale.  
  
##  <a name="AlterDb"></a> ALTER DATABASE … SET HADR …  
 Le opzioni della clausola [SET HADR](../../../t-sql/statements/alter-database-transact-sql-set-hadr.md) dell'istruzione ALTER DATABASE consentono di creare un join di un database secondario al gruppo di disponibilità del database primario corrispondente, di rimuovere un database unito in join, di sospendere la sincronizzazione dei dati in un database unito in join, nonché di riprendere la sincronizzazione dei dati.  
  
##  <a name="DropAG"></a> DROP AVAILABILITY GROUP  
 [DROP AVAILABILITY GROUP](../../../t-sql/statements/drop-availability-group-transact-sql.md) consente di rimuovere un gruppo di disponibilità specificato e tutte le relative repliche. DROP AVAILABILITY GROUP può essere eseguito da qualsiasi nodo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nel cluster di failover WSFC.  
  
##  <a name="Restrictions"></a> Restrictions on the AVAILABILITY GROUP Transact-SQL Statements  
 Le istruzioni di [!INCLUDE[tsql](../../../includes/tsql-md.md)] CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP e DROP AVAILABILITY GROUP presentano le limitazioni seguenti:  
  
-   Fatta eccezione per DROP AVAILABILITY GROUP, l'esecuzione di queste istruzioni richiede che il servizio HADR sia abilitato nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Abilitare e disabilitare la funzionalità Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Non è possibile eseguire queste istruzioni all'interno di transazioni o batch.  
  
-   Sebbene vengano fatti tentativi di ripulitura in seguito a un errore, queste istruzioni non garantiscono che sia possibile eseguire il rollback di tutte le modifiche in seguito a tale errore. Tuttavia, i sistemi dovrebbero essere in grado di gestire correttamente, e quindi ignorare, gli errori parziali.  
  
-   Queste istruzioni non supportano espressioni o variabili.  
  
-   Se viene eseguita un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] mentre è in corso un'altra azione o recupero del gruppo di disponibilità, verrà restituito un errore. Attendere che l'azione o il recupero siano stati completati e ritentare l'istruzione, se necessario.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
