---
title: Elemento (XMLA) del database | Microsoft Docs
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
- Database Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.database
- http://schemas.microsoft.com/analysisservices/2003/engine#Database
- urn:schemas-microsoft-com:xml-analysis#Database
helpviewer_keywords:
- Database element
ms.assetid: 2ded06c4-4eaf-4ccb-a416-41ee51ced8bc
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22e385380b2757427b5fa3a33725f6c25e8dde36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249431"
---
# <a name="database-element-xmla"></a>Elemento Database (XMLA)
  Identifica il database contenente la dimensione rappresentata dall'elemento padre [oggetto](object-element-dimension-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Object>  
   ...  
   <Database>...</Database>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Oggetto](object-element-dimension-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `Database` è un identificatore di oggetto contenente il nome del database di Analysis Services che contiene la dimensione rappresentata dall'elemento `Object`.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento del cubo &#40;XMLA&#41;](cube-element-xmla.md)   
 [Elemento della dimensione &#40;XMLA&#41;](dimension-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
