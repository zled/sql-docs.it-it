---
title: "Proprietà funzionalità | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0c12d59deb8a039ed5d8af5033d65e2614d4feb2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="feature-properties"></a>Proprietà di funzionalità
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Le proprietà della funzionalità relative alle funzionalità del prodotto, la maggior parte di essi avanzate, incluse le proprietà che controllano i collegamenti tra le istanze del server.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta le proprietà del server elencate nella tabella seguente. Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Si applica a:** solo in modalità server multidimensionale  
  
## <a name="properties"></a>Proprietà  
  
|Proprietà|Default|Description|  
|--------------|-------------|-----------------|  
|**ManagedCodeEnabled**|1|Proprietà booleana che indica se le procedure di archiviazione CLR sono abilitate.|  
|**LinkInsideInstanceEnabled**|1|Proprietà booleana che indica se è possibile creare un oggetto collegato all'interno della medesima istanza di server.|  
|**LinkToOtherInstanceEnabled**|0|Proprietà booleana che indica se è possibile creare collegamenti a oggetti situati su server remoti.|  
|**LinkFromOtherInstanceEnabled**|0|Proprietà booleana che indica se è possibile stabilire collegamenti ad oggetti da altre istanze di server.|  
|**ConnStringEncryptionEnabled**|1|Proprietà booleana che indica se la stringa di connessione è crittografata nel file di configurazione del server.|  
|**UseCachedPageAllocators**|0|Proprietà booleana che indica se gli allocatori di pagine memorizzati nella cache sono abilitati.|  
|**ComUdfEnabled**|0|Proprietà booleana che indica se le funzioni definite dall'utente come oggetti COM sono abilitate.|  
|**SQMSupportEnabled**|1|Proprietà booleana che indica se le segnalazioni sugli errori e sull'uso delle funzionalità vengono inviate automaticamente a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|  
|**ResourceMonitoringEnabled**|1|Proprietà booleana che indica se i contatori di monitoraggio delle risorse interne sono abilitati. Questa proprietà è attivata per impostazione predefinita. Quando è abilitata, la proprietà contente ai contatori di raccogliere dati di utilizzo relativi a CPU, memoria e attività di I/O.<br /><br /> I contatori di monitoraggio delle risorse interne vengono utilizzati dalle DMV (viste a gestione dinamica) per la creazione di report sull'utilizzo delle risorse. Se si disabilita questa proprietà, le query DMV continueranno a essere eseguite, tuttavia il set di risultati non sarà valido. Tra le DMV che dipendono da questa proprietà sono incluse le seguenti:<br /><br /> **DISCOVER_OBJECT_ACTIVITY**<br /><br /> **DISCOVER_COMMAND_OBJECTS**<br /><br /> **DISCOVER_SESSIONS** (per SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Nota: su un sistema multicore che utilizza l'architettura NUMA, la disabilitazione di questa proprietà può migliorare le prestazioni di esecuzione delle query, specialmente per carichi di lavoro multiutente elevati. Sarà necessario eseguire test di confronto per determinare se le prestazioni di esecuzione delle query vengono migliorate a seguito della modifica di questa proprietà. Per le procedure consigliate su come eseguire test di confronto, inclusi la cancellazione della cache e il modo di evitare errori comuni, vedere la pagina relativa alla [Guida operativa di SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Utilizzare DMV per monitorare Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
