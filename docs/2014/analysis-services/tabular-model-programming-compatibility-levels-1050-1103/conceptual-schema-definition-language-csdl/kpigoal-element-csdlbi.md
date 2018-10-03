---
title: Elemento KpiGoal (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ceee819fb887e2a45b3f366b261fba00df4776a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191381"
---
# <a name="kpigoal-element-csdlbi"></a>Elemento KpiGoal (CSDLBI)
  L'elemento KpiGoal fornisce un riferimento alla colonna utilizzata per definire l'obiettivo di un indicatore di prestazioni di chiave.  
  
 In CSDLB gli indicatori di prestazioni chiave sono basati sulle misure e l'elemento Measure contiene la formula (se presente), mentre gli altri metadati associati all'indicatore KPI sono definiti come parte dell'[elemento KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md).  L'elemento Kpigoal è un sottotipo dell'elemento KPI.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi che definiscono l'elemento KpiGoal.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Sì|Riferimento alla colonna che contiene il valore obiettivo KPI.<br /><br /> L'elemento Kpigoal deve contenere un solo elemento PropertyRef.<br /><br /> Vedere [Elemento PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md).|  
  
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
 [Elemento KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
  
