---
title: Attributo di elemento (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 68283f4d51bb01ed8b531b4d49e059b742663c26
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-element-xmla"></a>Elemento Attribute (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce o filtra un membro in un attributo in cui viene eseguito un comando padre [Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)o [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) .  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributi](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md), [Keys](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|[Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md), [CustomRollup](../../../analysis-services/xmla/xml-elements-properties/customrollup-element-xmla.md), [CustomRollupProperties](../../../analysis-services/xmla/xml-elements-properties/customrollupproperties-element-xmla.md), [Keys](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md), [Name](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md), [SkippedLevels](../../../analysis-services/xmla/xml-elements-properties/skippedlevels-element-xmla.md), [Translations](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md), [UnaryOperator](../../../analysis-services/xmla/xml-elements-properties/unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento **Attribute** definisce il membro dell'attributo inserito, aggiornato o eliminato rispettivamente dal comando **Insert**, **Update**o **Drop** . Poiché questi comandi possono operare solo in uno membro dell'attributo alla volta, il [attributi](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) insieme del **inserire**, **aggiornamento**, e **Drop**comandi possono contenere un solo **attributo** elemento. La raccolta **Attributes** dell'elemento **Where** per i comandi **Drop** e **Update** , tuttavia, può contenere più di un elemento **Attribute** , in modo che sia possibile filtrare gli attributi da eliminare o aggiornare in una dimensione abilitata per la scrittura.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)   
 [Dimensioni abilitate per scrittura](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
