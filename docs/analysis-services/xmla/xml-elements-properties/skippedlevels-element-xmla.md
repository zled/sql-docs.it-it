---
title: Elemento SkippedLevels (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3813ea7fd0d4936c458487ade9a3d81ad87ce09d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036509"
---
# <a name="skippedlevels-element-xmla"></a>Elemento SkippedLevels (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene il numero di livelli ignorati da un membro dell'attributo rappresentato dall'elemento padre [attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute>  
   ...  
   <SkippedLevels>...</SkippedLevels>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|0|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **SkippedLevels** elemento determina il numero di livelli ignorati da un membro dell'attributo definito dall'elemento padre **attributo** elemento.  
  
## <a name="see-also"></a>Vedere anche
 [Inserire l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
