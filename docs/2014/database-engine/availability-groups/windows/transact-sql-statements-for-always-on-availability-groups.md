---
title: Cenni preliminari sulle istruzioni Transact-SQL per i gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b0c766ed98bf5833790d2c0c1a35bfbff3c91e3c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208861"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a>Panoramica delle istruzioni Transact-SQL per i gruppi di disponibilità AlwaysOn (SQL Server)
  In questo argomento si introducono le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] che supportano la distribuzione di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , nonché la creazione e la gestione di qualsiasi gruppo, replica e database di disponibilità.  
  
  
##  <a name="CreateEndpoint"></a> CREATE ENDPOINT  
 [CREATE ENDPOINT … FOR DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql) consente di creare un endpoint del mirroring di database, se non ne esiste uno nell'istanza del server. Per ogni istanza del server in cui si intende distribuire [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] o il mirroring del database è necessario un endpoint di mirroring del database.  
  
 Eseguire questa istruzione sull'istanza del server nella quale si crea l'endpoint. È possibile creare solo un endpoint del mirroring del database in una determinata istanza del server. Per altre informazioni, vedere [Endpoint del mirroring del database &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
##  <a name="CreateAG"></a> CREATE AVAILABILITY GROUP  
 Con[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) è possibile creare un nuovo gruppo di disponibilità e, facoltativamente, un listener del gruppo di disponibilità. È necessario specificare almeno l'istanza del server locale, che diventerà la replica primaria iniziale. È eventualmente possibile specificare anche un massimo di quattro repliche secondarie.  
  
 Eseguire CREATE AVAILABILITY GROUP nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui si desidera ospitare la replica primaria iniziale del nuovo gruppo di disponibilità. Questa istanza del server deve trovarsi in un nodo di un Failover del Cluster WSFC (Windows Server) (per altre informazioni, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="AlterAG"></a> ALTER AVAILABILITY GROUP  
 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) supporta la modifica di un gruppo di disponibilità o di un listener del gruppo di disponibilità esistente, nonché l'esecuzione del failover di un gruppo di disponibilità.  
  
 Eseguire ALTER AVAILABILITY GROUP nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui è ospitata la replica primaria iniziale.  
  
##  <a name="AlterDb"></a> ALTER DATABASE … SET HADR …  
 Le opzioni della clausola [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) dell'istruzione ALTER DATABASE consentono di creare un join di un database secondario al gruppo di disponibilità del database primario corrispondente, di rimuovere un database unito in join, di sospendere la sincronizzazione dei dati in un database unito in join, nonché di riprendere la sincronizzazione dei dati.  
  
##  <a name="DropAG"></a> DROP AVAILABILITY GROUP  
 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) consente di rimuovere un gruppo di disponibilità specificato e tutte le relative repliche. DROP AVAILABILITY GROUP può essere eseguito da qualsiasi nodo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nel cluster di failover WSFC.  
  
##  <a name="Restrictions"></a> Restrictions on the AVAILABILITY GROUP Transact-SQL Statements  
 Le istruzioni di [!INCLUDE[tsql](../../../includes/tsql-md.md)] CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP e DROP AVAILABILITY GROUP presentano le limitazioni seguenti:  
  
-   Fatta eccezione per DROP AVAILABILITY GROUP, l'esecuzione di queste istruzioni richiede che il servizio HADR sia abilitato nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Abilitare e disabilitare la funzionalità Gruppi di disponibilità Always On &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Non è possibile eseguire queste istruzioni all'interno di transazioni o batch.  
  
-   Sebbene vengano fatti tentativi di ripulitura in seguito a un errore, queste istruzioni non garantiscono che sia possibile eseguire il rollback di tutte le modifiche in seguito a tale errore. Tuttavia, i sistemi dovrebbero essere in grado di gestire correttamente, e quindi ignorare, gli errori parziali.  
  
-   Queste istruzioni non supportano espressioni o variabili.  
  
-   Se viene eseguita un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] mentre è in corso un'altra azione o recupero del gruppo di disponibilità, verrà restituito un errore. Attendere che l'azione o il recupero siano stati completati e ritentare l'istruzione, se necessario.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
