---
title: Elemento DataSourceView (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataSourceView Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceView
- microsoft.xml.analysis.datasourceview
- urn:schemas-microsoft-com:xml-analysis#DataSourceView
helpviewer_keywords: DataSourceView element
ms.assetid: c4a4360f-7342-484b-bac1-0a247e8f279d
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c1f5a81358b182a595cbb4e7a98b50db1a7ce460
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="datasourceview-element-xmla"></a>Elemento DataSourceView (XMLA)
  Contiene una vista origine dati out-of-line associazione per l'elemento padre [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) o [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <DataSourceView>  
      <DatabaseID>...</DatabaseID>  
      <DataSourceViewID>...</DataSourceViewID>  
   </DataSourceView>  
...  
</Batch>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md), [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Elementi figlio|[DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [DataSourceViewID](../../../analysis-services/scripting/properties/datasourceviewid-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **DataSourceView** elemento rappresenta un'associazione out-of-line a una vista origine dati, utilizzata dal **Batch** o **processo** comando per eseguire temporaneamente l'override dell'origine dati visualizzare l'associazione per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oggetti elaborati dal comando.  
  
 Per ulteriori informazioni sulle associazioni out-of-line, vedere [origini dati e associazioni &#40; SSAS multidimensionale &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
