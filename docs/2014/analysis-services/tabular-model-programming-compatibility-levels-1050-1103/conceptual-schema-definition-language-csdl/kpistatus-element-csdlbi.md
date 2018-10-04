---
title: Elemento KpiStatus (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 6fee5b82-caa8-46a1-ad68-bbce3e11e01e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab554d47678b336ebfa763a7f3bd05f027e92945
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164541"
---
# <a name="kpistatus-element-csdlbi"></a>Elemento KpiStatus (CSDLBI)
  L'elemento KpiStatus definisce un rifermento alla colonna contenente il valore utilizzato come indicatore di stato in un indicatore di prestazioni di chiave.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento KpiStatus.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Sì|Riferimento a una colonna contenente il valore utilizzato come indicatore di stato in un indicatore KPI.<br /><br /> Questo elemento DEVE contenere una sola colonna di riferimento, come definito dal tipo TPropertyRefcomplex.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrato un indicatore KPI del modello tabulare di esempio di AdventureWorks. L'elemento KpiStatus fa riferimento a una colonna (rappresentata come PropertyRef) contenente il valore.  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
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
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato un indicatore KPI del cubo Operations di Contoso. L'elemento KpiStatus fa riferimento a una misura che calcola il valore dello stato dell'indicatore KPI.  
  
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
  
  
