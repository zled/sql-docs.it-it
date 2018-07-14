---
title: Elemento Translation (XMLA) | Microsoft Docs
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
- Translation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Translation
- microsoft.xml.analysis.translation
- http://schemas.microsoft.com/analysisservices/2003/engine#Translation
helpviewer_keywords:
- Translation element
ms.assetid: ce962d4b-dda9-4a16-a56c-ff7a5275c48a
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ce94966eae0cb1088ff462f551bdd27ad4304ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180788"
---
# <a name="translation-element-xmla"></a>Elemento Translation (XMLA)
  Definisce una traduzione per un membro attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Translations>  
   ...  
   <Translation>  
      <Language>...</Language>  
      <Name>...</Name>  
   </Translation>  
   ...  
</Translations>  
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
|Elementi padre|[Traduzioni](translations-element-xmla.md)|  
|Elementi figlio|[Linguaggio](language-element-xmla.md), [nome](name-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Oggetto `Translation` elemento definisce le informazioni necessarie per associare un membro dell'attributo a una traduzione definita per un attributo specificato durante un [inserire](../xml-elements-commands/insert-element-xmla.md) oppure [Update](../xml-elements-commands/update-element-xmla.md) comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
