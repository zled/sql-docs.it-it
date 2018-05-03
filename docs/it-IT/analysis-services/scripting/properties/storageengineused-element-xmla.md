---
title: Elemento StorageEngineUsed (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- StorageEngineUsed Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
ms.assetid: 98895c10-f3c2-4d8a-be94-6128c828561d
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bbd29ac3caec5f82e34c116125d7b43b4088fc15
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="storageengineused-element-xmla"></a>Elemento StorageEngineUsed (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene un valore di sola lettura che descrive il tipo di database corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Databases>  
      <Database>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastUpdate>...</LastUpdate>  
      <Description>...</Description>  
      <State>   </State>  
      <AggregationPrefix>...</AggregationPrefix>  
      <EstimatedSize>...</EstimatedSize>  
      <LastProcessed>...</LastProcessed>  
      <Language>...</Language>  
            <Collation>...</Collation>  
            <Visible>...</Visible>  
      <MasterDatasourceID>...</MasterDataSourceID>  
      <Accounts>...</Accounts>  
      <DataSources>...</DataSources>  
      <DataSourceViews>...</DataSourceViews>  
            <Dimensions>...</Dimensions>  
      <Cubes>...</Cubes>  
            <MiningStructures>...</MiningStructures>  
      <Roles>...</Roles>  
      <Assemblies>...</Assemblies>  
      <DatabasePermissions>...</DatabasePermissions>  
      <Translations>...</Translations>  
      <Annotations>...</Annotations>  
            <StorageEngineUsed >...</StorageEngineUsed>  
   </Database>  
</Databases>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[database](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Tradizionale*|Il modello di database corrisponde a una modalità di archiviazione MOLAP, ROLAP o HOLAP.|  
|*InMemory*|Il modello di database corrisponde a una modalità di archiviazione IMBI.|  
|*Mista*|Il modello di database unisce le modalità di archiviazione IMBI e MOLAP, ROLAP o HOLAP.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **StorageEngineUsed** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.StorageEngineUsed>.  
  
 Gli elementi che corrispondono ai padri di **StorageEngineUsed** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.Database>.  
  
  
