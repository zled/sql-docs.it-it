---
title: Il tipo di dati EventColumn (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe9daba9906a3bc65bfd33e87f07ef55615734cb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="eventcolumn-data-type-assl"></a>Tipo di dati EventColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo che rappresenta una colonna di informazioni da acquisire per un elemento [Event](../../../analysis-services/scripting/objects/event-element-assl.md) come parte di un elemento [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[ColumnID](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md)|  
|Elementi derivati|[Colonna](../../../analysis-services/scripting/objects/column-element-assl.md) ([le colonne](../../../analysis-services/scripting/collections/columns-element-assl.md) insieme [traccia](../../../analysis-services/scripting/objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Events &#40;ASSL&#41;](../../../analysis-services/scripting/collections/events-element-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
