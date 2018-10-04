---
title: Attributo a elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Attribute Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords:
- Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7baad7e154cda5ce52e67f08af46e7344f6af1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128211"
---
# <a name="attribute-element-xmla"></a>Elemento Attribute (XMLA)
  Definisce o filtra un membro in un attributo in cui un elemento padre [inserire](../xml-elements-commands/insert-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md), o [Drop](../xml-elements-commands/drop-element-xmla.md) comando esegue.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attributes>  
   ...  
   <Attribute>  
      <AttributeName>...</AttributeName>  
      <Keys>...</Keys>  
      <!-- The following elements are included only for attributes contained in the Attributes element of a parent Insert or Update command -->  
      <Name>...</Name>  
      <Translations>...</Translations>  
      <CustomRollup>...</CustomRollup>  
      <CustomRollupProperties>...</CustomRollupProperties>  
      <UnaryOperator>...</UnaryOperator>  
      <SkippedLevels>...</SkippedLevels>  
   </Attribute>  
   ...  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributi](attributes-element-xmla.md)|  
  
 **Elementi figlio**  
  
|||  
|-|-|  
|**Predecessore o padre**|**Elemento figlio**|  
|[DROP](../xml-elements-commands/drop-element-xmla.md), [in cui](name-element-xmla.md), [chiavi](keys-element-xmla.md)|  
|[Inserire](../xml-elements-commands/insert-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md)|[AttributeName](name-element-xmla.md), [CustomRollup](customrollup-element-xmla.md), [CustomRollupProperties](properties-element-xmla.md), [chiavi](keys-element-xmla.md), [nome](name-element-xmla.md), [ SkippedLevels](skippedlevels-element-xmla.md), [traduzioni](translations-element-xmla.md), [UnaryOperator](unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il `Attribute` elemento definisce il membro dell'attributo inserito, aggiornato o eliminato, rispettivamente, con il `Insert`, `Update`, o `Drop` comando. Poiché questi comandi possono operare solo in uno membro dell'attributo alla volta, il [attributi](attributes-element-xmla.md) insieme delle `Insert`, `Update`, e `Drop` comandi possono contenere un solo `Attribute` elemento. La raccolta `Attributes` dell'elemento `Where` per i comandi `Drop` e `Update`, tuttavia, può contenere più di un elemento `Attribute`, in modo che sia possibile filtrare gli attributi da eliminare o aggiornare in una dimensione abilitata per la scrittura.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)   
 [Dimensioni abilitate per la scrittura](../../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
