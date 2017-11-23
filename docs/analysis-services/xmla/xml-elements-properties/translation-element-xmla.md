---
title: Elemento Translation (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
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
ms.openlocfilehash: 33ffa6460f843949ec0e4b5659f614a036fdf0a1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Traduzioni](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md)|  
|Elementi figlio|[Lingua](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md), [nome](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **traduzione** elemento definisce le informazioni necessarie per associare un membro dell'attributo a una traduzione definita per un determinato attributo durante un [inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) o [aggiornamento](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
