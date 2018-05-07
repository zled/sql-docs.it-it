---
title: Dati Cubebinding (out-of-line) (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74a782f551ad31e583c5d9fd33d02f7d975ec7b8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>Tipo di dati CubeBinding (out-of-line) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo che rappresenta la relazione tra un elemento [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) e un elemento [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeBinding>  
   <ID>...</ID>  
   <DataSourceID>...</DataSourceID>  
   <DataSource>...</DataSource>  
   <MeasureGroup>...</MeasureGroup>  
</CubeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Elementi derivati|[Binding](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) (raccolta[Bindings](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md) di comandi [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) o [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) )|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sulle associazioni out-of-line, vedere [origini dati e associazioni & #40; SSAS multidimensionale & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
