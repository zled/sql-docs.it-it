---
title: Elemento Translation (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Translation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Translation
- microsoft.xml.analysis.translation
- http://schemas.microsoft.com/analysisservices/2003/engine#Translation
helpviewer_keywords: Translation element
ms.assetid: ce962d4b-dda9-4a16-a56c-ff7a5275c48a
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 22f20acf00a8bce0218011ab6f4b08791020175e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="translation-element-xmla"></a>Elemento Translation (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Definisce una traduzione per un membro dell'attributo.  
  
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
|Elementi padre|[Traduzioni](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md)|  
|Elementi figlio|[Lingua](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md), [nome](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Oggetto **traduzione** elemento definisce le informazioni necessarie per associare un membro dell'attributo a una traduzione definita per un determinato attributo durante un [inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) o [aggiornamento](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
