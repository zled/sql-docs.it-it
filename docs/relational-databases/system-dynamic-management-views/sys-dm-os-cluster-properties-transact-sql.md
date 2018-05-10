---
title: Sys.dm os_cluster_properties (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_cluster_properties_TSQL
- sys.dm_os_cluster_properties
- dm_os_cluster_properties_TSQL
- dm_os_cluster_properties
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_cluster_properties
- sys.dm_os_cluster_properties
ms.assetid: 6d82e770-fba7-49e0-9a0c-3b34b393e4a7
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0547df42a00699539bde5a8fe918d97b61f63371
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosclusterproperties-transact-sql"></a>sys.dm_os_cluster_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga con le impostazioni correnti per le proprietà delle risorse cluster di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificate in questo argomento. Non verrà restituito alcun dato se questa vista viene eseguita in un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Queste proprietà vengono utilizzate per impostare i valori che influiscono sul rilevamento degli errori, sui tempi di risposta agli errori e sulla registrazione per il monitoraggio dello stato integrità dell'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  

|Nome colonna|Proprietà|Description|  
|-----------------|--------------|-----------------|  
|VerboseLogging|bigint|Livello di registrazione per il cluster di failover di SQL Server. La registrazione dettagliata può essere attivata per fornire dettagli aggiuntivi nei log degli errori per la risoluzione dei problemi. I valori validi sono:<br /><br /> 0: la registrazione è disabilitata (impostazione predefinita)<br /><br /> 1: solo errori<br /><br /> 2: errori e avvisi<br /><br /> Per altre informazioni, vedere [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md).|  
|SqlDumperDumpFlags|bigint|I flag di dump di SQLDumper determinano il tipo dei file di dump generati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'impostazione predefinita è 0.|  
|SqlDumperDumpPath|nvarchar(260)|Percorso in cui l'utilità SQLDumper genera i file di dump.|  
|SqlDumperDumpTimeOut|bigint|Valore di timeout in millisecondi prima che l'utilità SQLDumper generi un dump in caso di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il valore predefinito è 0.|  
|FailureConditionLevel|bigint|Consente di impostare le condizioni in cui il cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve restituire un errore o essere riavviato. Il valore predefinito è 3. Per una spiegazione dettagliata o per modificare le impostazioni delle proprietà, vedere [configurare le impostazioni della proprietà FailureConditionLevel](../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md).|  
|HealthCheckTimeout|bigint|Valore di timeout che consente di definire il tempo di attesa da parte della DLL risorse del motore di database di SQL Server relativo alla restituzione delle informazioni sull'integrità del server prima che venga stabilita la mancata risposta dell'istanza di SQL Server. Il valore di timeout è espresso in millisecondi. Valore predefinito è 60000. Per ulteriori informazioni o per modificare questa impostazione di proprietà, vedere [configurazione delle impostazioni HealthCheckTimeout](../../sql-server/failover-clusters/windows/configure-healthchecktimeout-property-settings.md).|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede le autorizzazioni VIEW SERVER STATE sull'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato sys.dm_os_cluster_properties per restituire le impostazioni della proprietà per la risorsa cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT VerboseLogging, SqlDumperDumpFlags, SqlDumperDumpPath, SqlDumperDumpTimeOut, FailureConditionLevel, HealthCheckTimeout  
FROM sys.dm_os_cluster_properties;  
```  
  
 Set di risultati di esempio:  
  
|VerboseLogging|SqlDumperDumpFlags|SqlDumperDumpPath|SqlDumperDumpTimeOut|FailureConditionLevel|HealthCheckTimeout|  
|--------------------|------------------------|-----------------------|--------------------------|---------------------------|------------------------|  
|0|0|NULL|0|3|60000|  
  
  
