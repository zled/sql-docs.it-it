---
title: Data Mining Schema Rowsets | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9302e8dbafd31f4efb3b053ea5247f2b860dc8bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066184"
---
# <a name="data-mining-schema-rowsets"></a>Set di righe dello schema di data mining
  Un server che esegue [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta i seguenti set di righe dello schema di data mining. Per verificare se un determinato provider XML/A supporta un set di righe specifico, utilizzare il [DISCOVER_ENUMERATORS](../xml/discover-enumerators-rowset.md) set di righe con il [Discover](../../xmla/xml-elements-methods-discover.md) metodo.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] i set di righe dello schema di data mining vengono esposti come tabelle nel linguaggio Transact-SQL nello schema $SYSTEM. Ad esempio, la query seguente su un'istanza di Analysis Services restituisce un elenco degli schemi disponibili sull'istanza corrente.  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Set di righe dello schema|Description|  
|-------------------|-----------------|  
|[Set di righe DMSCHEMA_MINING_COLUMNS](dmschema-mining-columns-rowset.md)|Descrive le singole colonne di tutti i modelli di data mining definiti distribuiti nel server.|  
|[Set di righe DMSCHEMA_MINING_FUNCTIONS](dmschema-mining-functions-rowset.md)|Descrive le funzioni di stima e di estrazione che è possibile utilizzare con ogni algoritmo di data mining installato nel server.|  
|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT](dmschema-mining-model-content-rowset.md)|Consente alle applicazioni client di esplorare il contenuto di un modello di data mining sottoposto a training.|  
|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML](dmschema-mining-model-content-pmml-rowset.md)|Restituisce la rappresentazione XML (PMML 2.1) del contenuto del modello di data mining.|  
|[Set di righe DMSCHEMA_MINING_MODEL_XML](dmschema-mining-model-xml-rowset.md)|Restituisce la struttura XML (PMML 2.1) del modello di data mining. Si tratta dello stesso schema di DMSCHEMA_MINING_MODEL_PMML, che viene mantenuto per garantire la compatibilità con le versioni precedenti.|  
|[Set di righe DMSCHEMA_MINING_MODELS](dmschema-mining-models-rowset.md)|Enumera i modelli di data mining distribuiti nel server.|  
|[Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS](dmschema-mining-service-parameters-rowset.md)|Fornisce un elenco dei parametri che è possibile utilizzare per configurare il comportamento di ogni algoritmo di data mining installato nel server.|  
|[Set di righe DMSCHEMA_MINING_SERVICES](dmschema-mining-services-rowset.md)|Fornisce una descrizione di ogni algoritmo di data mining disponibile nel server.|  
|[Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS](dmschema-mining-structure-columns-rowset.md)|Descrive le singole colonne di tutte le strutture di data mining distribuite nel server.|  
|[Set di righe DMSCHEMA_MINING_STRUCTURES](dmschema-mining-structures-rowset.md)|Enumera informazioni sulle strutture di data mining.|  
  
 Tutte le righe dello schema elencati di seguito sono supportate dal server che esegue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [L'esecuzione di query il catalogo di sistema SQL Server](https://technet.microsoft.com/en-us/library/ms189082\(v=sql.110\).aspx)   
 [L'esecuzione di query di Data Mining rowset dello Schema &#40;Analysis Services - Data Mining&#41;](../../data-mining/data-mining-schema-rowsets-ssas.md)  
  
  