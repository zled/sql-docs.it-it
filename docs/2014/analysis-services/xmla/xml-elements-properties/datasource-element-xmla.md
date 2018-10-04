---
title: Elemento DataSource (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSource Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSource
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSource
- microsoft.xml.analysis.datasource
helpviewer_keywords:
- DataSource element
ms.assetid: adc0713a-3927-40f3-8b87-012130908f34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3acbba2e1ee5df1535799e133c064b90b6921386
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130527"
---
# <a name="datasource-element-xmla"></a>Elemento DataSource (XMLA)
  Contiene un'associazione all'origine dati out-of-line per l'elemento padre [Batch](../xml-elements-commands/batch-element-xmla.md) oppure [processo](../xml-elements-commands/process-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <DataSource>  
      <DatabaseID>...</DatabaseID>  
      <DataSourceID>...</DataSourceID>  
   </DataSource>  
...  
</Batch>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Batch](../xml-elements-commands/batch-element-xmla.md), [processo](../xml-elements-commands/process-element-xmla.md)|  
|Elementi figlio|[DatabaseID](id-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il `DataSource` elemento rappresenta un'associazione out-of-line a un'origine dati, utilizzata per il `Batch` o `Process` comando per eseguire temporaneamente l'override l'associazione all'origine dati per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oggetti elaborati dal comando.  
  
 Per altre informazioni sulle associazioni out-of-line, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
