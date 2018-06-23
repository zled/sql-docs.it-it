---
title: Elemento LastSchemaUpdate (XMLA) | Documenti Microsoft
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
- LastSchemaUpdate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#LastSchemaUpdate
- urn:schemas-microsoft-com:xml-analysis#LastSchemaUpdate
- microsoft.xml.analysis.lastschemaupdate
helpviewer_keywords:
- LastSchemaUpdate element
ms.assetid: 2109955c-2817-413e-93aa-95d9910e8b24
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 88bd4b0a271b8fd59538211ae3bc22519c7052d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166923"
---
# <a name="lastschemaupdate-element-xmla"></a>Elemento LastSchemaUpdate (XMLA)
  Contiene la data e l'ora dell'ultimo aggiornamento dei metadati del cubo rappresentato dall'elemento padre [Cube](cube-element-olapinfo-xmla.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube>  
   ...  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|dateTime|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cube](cube-element-olapinfo-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  