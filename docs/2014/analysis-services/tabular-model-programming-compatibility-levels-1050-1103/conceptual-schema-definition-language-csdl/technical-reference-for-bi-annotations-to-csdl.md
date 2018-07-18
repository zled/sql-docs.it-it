---
title: Riferimento tecnico per annotazioni di Business Intelligence per CSDL | Documenti Microsoft
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
ms.assetid: 63b3e069-6ba5-474e-b769-47b7cc87b7dd
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 27ed1339d64dd3c4035288a96b31ae163a304733
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064990"
---
# <a name="technical-reference-for-bi-annotations-to-csdl"></a>Riferimento tecnico per le annotazioni di Business Intelligence per CSDL
  In questa sezione vengono elencati gli elementi, l'attributo e le proprietà in CSDL utilizzati per rappresentare i modelli tabulari di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Alcuni elementi sono nuovi, altri sono stati annotati o estesi per supportare la modellazione di Business Intelligence.  
  
 Per una panoramica dei modelli tabulari e modo in cui sono rappresentate le entità, relazioni e formule in CSDL, vedere [annotazioni CSDL per Business Intelligence &#40;CSDLBI&#41;](../csdl-annotations-for-business-intelligence-csdlbi.md).  
  
## <a name="extended-csdl-elements-complex-types"></a>Elementi estesi CSDL: tipi complessi  
 I seguenti elementi CSDL sono stati aggiunti o estesi per supportare modelli di dati tabulari e multidimensionali di Business Intelligence.  
  
-   [Elemento AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)  
  
-   [Elemento BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [Elemento DefaultDetails &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)  
  
-   [Elemento DisplayKey &#40;CSDLBI&#41;](displaykey-element-csdlbi.md)  
  
-   [Elemento EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)  
  
-   [Elemento EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
-   [Elemento EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)  
  
-   [Elemento Hierarchy &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)  
  
-   [Elemento KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
-   [Elemento KpiGoal &#40;CSDLBI&#41;](kpigoal-element-csdlbi.md)  
  
-   [Elemento KpiStatus &#40;CSDLBI&#41;](kpistatus-element-csdlbi.md)  
  
-   [Livello di elemento &#40;CSDLBI&#41;](level-element-csdlbi.md)  
  
-   [Elemento di misure &#40;CSDLBI&#41;](measure-element-csdlbi.md)  
  
-   [Elemento membro &#40;CSDLBI&#41;](member-element-csdlbi.md)  
  
-   [Elemento MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md)  
  
-   [Elemento NavigationProperty &#40;CSDLBI&#41;](navigationproperty-element-csdlbi.md)  
  
-   [Elemento della proprietà &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [Elemento PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)  
  
## <a name="simple-type-and-subtypes"></a>Tipo semplice e sottotipi  
 Nella tabella seguente sono elencati alcuni tipi semplici e alcuni tipi complessi secondari che sono inclusi nelle definizioni dei tipi complessi elencati in precedenza. La documentazione per ogni tipo semplice o sottotipo elencato nella colonna di sinistra è disponibile negli elementi padre elencati nella colonna destra.  
  
|Tipo semplice|Presente nell'argomento|  
|-----------------|--------------------|  
|Alignment|[Elemento BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|CompareOptions|[Elemento EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|Sommario|[Elemento EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)|  
|ContextualNameRule|[Elemento membro &#40;CSDLBI&#41;](member-element-csdlbi.md)|  
|DefaultAggregationFunction|[Elemento della proprietà &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|DirectQueryMode|[Elemento EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|GroupingBehavior|[Elemento della proprietà &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|MemberRefs|[Elemento MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md)|  
|PropertyRefs|[Elemento PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)|  
|SortDirection|[Elemento BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|State|[Elemento AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
|Stability|[Elemento della proprietà &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|SortDirection|[Elemento BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti di CSDLBI](../csdlbi-concepts.md)  
  
  