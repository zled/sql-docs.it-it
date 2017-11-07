---
title: Elemento KpiGoal (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c962ce78a66f862424ee3f4c0377cee2d0dabc0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="kpigoal-element-csdlbi"></a>Elemento KpiGoal (CSDLBI)
  L'elemento KpiGoal fornisce un riferimento alla colonna utilizzata per definire l'obiettivo di un indicatore di prestazioni di chiave.  
  
 In CSDLB gli indicatori di prestazioni chiave sono basati sulle misure e l'elemento Measure contiene la formula (se presente), mentre gli altri metadati associati all'indicatore KPI sono definiti come parte dell'[elemento KPI &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md).  L'elemento Kpigoal è un sottotipo dell'elemento KPI.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi che definiscono l'elemento KpiGoal.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Sì|Riferimento alla colonna che contiene il valore obiettivo KPI.<br /><br /> L'elemento Kpigoal deve contenere un solo elemento PropertyRef.<br /><br /> Vedere [Elemento PropertyRef &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md).|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrato un indicatore KPI del modello di esempio di AdventureWorks.  
  
```  
  
<Property Name="InternetCurrentSalesPerformance" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato un indicatore KPI del cubo Operations di Contoso.  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento KPI &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
  

