---
title: Elemento DesignAggregations (XMLA) | Documenti Microsoft
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
api_name:
- DesignAggregations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords:
- DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d448a7cc815dddcc4e9568831f2d652fc7a22680
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169746"
---
# <a name="designaggregations-element-xmla"></a>Elemento DesignAggregations (XMLA)
  Crea aggregazioni per una progettazione delle aggregazioni in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <DesignAggregations>  
      <Object>...</Object>  
      <Time>...</Time>  
      <Steps>...</Steps>  
      <Optimization>...</Optimization>  
      <Storage>...</Storage>  
      <Materialize>...</Materialize>  
      <Queries>...</Queries>  
   </DesignAggregations>  
</Command>  
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
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Materializza](../xml-elements-properties/materialize-element-xmla.md), [oggetto](../xml-elements-properties/object-element-xmla.md), [ottimizzazione](../xml-elements-properties/optimization-element-xmla.md), [query](../xml-elements-properties/queries-element-xmla.md), [passaggi](../xml-elements-properties/steps-element-xmla.md), [archiviazione](../xml-elements-properties/storage-element-xmla.md) , [Ora](../xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Il comando `DesignAggregations` viene utilizzato per generare definizioni di aggregazione archiviate da una progettazione delle aggregazioni. Una progettazione delle aggregazioni può essere quindi utilizzata per materializzare le aggregazioni per una partizione e può essere riutilizzata tra partizioni.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  