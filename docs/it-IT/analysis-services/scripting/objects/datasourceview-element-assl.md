---
title: Elemento DataSourceView (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- DataSourceView Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataSourceView
helpviewer_keywords:
- DataSourceView element
ms.assetid: cda26126-8af2-4519-8237-f4a57976a284
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5a419bc7b2f87bb5de1a90830dd1fa7655d61b4d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="datasourceview-element-assl"></a>Elemento DataSourceView (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce una vista origine dati utilizzata da un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [Database](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSourceViews>  
   <DataSourceView>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Annotations>...</Annotations>  
      <DataSourceID>   </DataSourceID>  
      <Schema>...</Schema>  
   </DataSourceView>  
</DataSourceViews>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DataSourceViews](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md)|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [ LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [dello Schema](../../../analysis-services/scripting/properties/schema-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
