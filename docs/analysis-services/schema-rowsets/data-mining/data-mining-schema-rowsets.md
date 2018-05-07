---
title: Data Mining Schema Rowsets | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ee1f8d3288d884f7322fa578d8cd9b58919c335b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
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
 [Dati i rowset dello Schema di Data Mining &#40;SSAs&#41;](../../../analysis-services/data-mining/data-mining-schema-rowsets-ssas.md)  
  
  
