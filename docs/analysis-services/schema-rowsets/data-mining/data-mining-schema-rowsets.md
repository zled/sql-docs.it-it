---
title: Data Mining Schema Rowsets | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: de34fa80e547b38216ca83458501347888488774
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="data-mining-schema-rowsets"></a>Set di righe dello schema di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Un server che esegue [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta i seguenti set di righe dello schema di data mining. Per verificare se un determinato provider XML/A supporta un set di righe specifico, utilizzare il [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) set di righe con la [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] i set di righe dello schema di data mining vengono esposti come tabelle nel linguaggio Transact-SQL nello schema $SYSTEM. Ad esempio, la query seguente su un'istanza di Analysis Services restituisce un elenco degli schemi disponibili sull'istanza corrente.  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Set di righe dello schema|Description|  
|-------------------|-----------------|  
|[Set di righe DMSCHEMA_MINING_COLUMNS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|Descrive le singole colonne di tutti i modelli di data mining definiti distribuiti nel server.|  
|[Set di righe DMSCHEMA_MINING_FUNCTIONS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|Descrive le funzioni di stima e di estrazione che è possibile utilizzare con ogni algoritmo di data mining installato nel server.|  
|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|Consente alle applicazioni client di esplorare il contenuto di un modello di data mining sottoposto a training.|  
|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|Restituisce la rappresentazione XML (PMML 2.1) del contenuto del modello di data mining.|  
|[Set di righe DMSCHEMA_MINING_MODEL_XML](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|Restituisce la struttura XML (PMML 2.1) del modello di data mining. Si tratta dello stesso schema di DMSCHEMA_MINING_MODEL_PMML, che viene mantenuto per garantire la compatibilità con le versioni precedenti.|  
|[Set di righe DMSCHEMA_MINING_MODELS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|Enumera i modelli di data mining distribuiti nel server.|  
|[Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|Fornisce un elenco dei parametri che è possibile utilizzare per configurare il comportamento di ogni algoritmo di data mining installato nel server.|  
|[Set di righe DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|Fornisce una descrizione di ogni algoritmo di data mining disponibile nel server.|  
|[Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|Descrive le singole colonne di tutte le strutture di data mining distribuite nel server.|  
|[Set di righe DMSCHEMA_MINING_STRUCTURES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|Enumera informazioni sulle strutture di data mining.|  
  
 Tutte le righe dello schema elencate di seguito sono supportate dal server in cui è in esecuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Set di righe dello Schema di Data Mining &#40; SSAs &#41;](../../../analysis-services/data-mining/data-mining-schema-rowsets-ssas.md)  
  
  
