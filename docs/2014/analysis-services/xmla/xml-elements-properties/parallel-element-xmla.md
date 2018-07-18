---
title: Elemento (XMLA) in parallelo | Microsoft Docs
ms.custom: ''
ms.date: 2015-12-07
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Parallel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parallel
- http://schemas.microsoft.com/analysisservices/2003/engine#Parallel
- microsoft.xml.analysis.parallel
helpviewer_keywords:
- Parallel element
ms.assetid: 04726d94-37ee-460b-9744-d62b45f536b9
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b514732345cc8c4c7c0bc2c2f4f3fa0ad2d75993
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161022"
---
# <a name="parallel-element-xmla"></a>Parallel Element (XMLA)
  Identifica i comandi da eseguire in parallelo tramite il comando padre [Batch](../xml-elements-commands/batch-element-xmla.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Batch>  
   ....  
   <Parallel maxParallel="Integer">  
      <!-- One or more XMLA commands -->  
   </Parallel>  
   ....  
</Batch>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Batch](../xml-elements-commands/batch-element-xmla.md)|  
|Elementi figlio|[Elemento Process](../xml-elements-commands/process-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|maxParallel|Facoltativo `Integer` attributo. Indica il numero massimo di thread in cui eseguire comandi in parallelo. Se omesso o impostato su 0, l'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] determina un numero ottimale di thread basato sul numero di processori disponibili nel computer.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
