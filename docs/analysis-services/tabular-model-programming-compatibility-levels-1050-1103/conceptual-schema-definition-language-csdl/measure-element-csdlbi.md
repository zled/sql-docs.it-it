---
title: Misure di elemento (CSDLBI) | Documenti Microsoft
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
ms.assetid: bfbc9274-053a-421a-bb81-2095bba710be
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ee1d1fdcdd17b9ade86e9f9acc6b6a41ed9cc930
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="measure-element-csdlbi"></a>Elemento Measure (CSDLBI)
  L'elemento Measure è un tipo complesso basato sull'elemento Property di CSDL. Le annotazioni CSDLBI aggiungono gli attributi che supportano la definizione delle formule complesse da utilizzare nei modelli di dati di Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli elementi e gli attributi che definiscono l'elemento Measure, oltre agli attributi applicabili all'elemento Property.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Kpi|No|Elemento obbligatorio solo per le misure utilizzate come indicatori KPI. Non tutte le misure sono indicatori KPI, ma tutti gli indicatori KPI devono essere basati sulla definizione di una misura.<br /><br /> [Elemento KPI &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)|  
|IsSimpleMeasure|No|Valore true/false che indica se la formula utilizzata nella misura è o meno un'aggregazione semplice (SUM, COUNT, MIN, MAX, AVG, DistinctCount).<br /><br /> Il valore predefinito è true.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, vengono illustrate due misure del modello tabulare di esempio di AdventureWorks. La seconda misura è stata convertita in un indicatore KPI, aggiungendo elementi KPI.  
  
```  
  
<Property   
    Name="Order_Lines_Count"   
    Type="Int64">  
<bi:Measure   
    Caption="Order Lines Count"   
    ReferenceName="Order Lines Count"   
    Width="0"   
    IsSimpleMeasure="false" />  
</Property>  
  
<Property   
    Name="Total_Current_Quarter_Sales_Performance"   
    Type="Double">  
<bi:Measure   
    Caption="Total Current Quarter Sales Performance"   
    ReferenceName="Total Current Quarter Sales Performance"   
    Width="0"   
    IsSimpleMeasure="false">  
    <bi:Kpi   
    StatusGraphic="Three Signs Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Goal_" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Status_" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensiona;**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportata una misura del cubo Operations di Contoso che è stata utilizzata come indicatore KPI.  
  
```  
  
<Property   
    Name="Sum_of_SalesAmount"   
    Type="Decimal" Precision="19" Scale="4">  
<Documentation>  
<Summary>KPI Description</Summary>  
</Documentation>  
<bi:Measure   
    Caption="Sum of SalesAmount"   
    ReferenceName="Sum of SalesAmount"   
    FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
<bi:Kpi   
    StatusGraphic="Three Circles Colored">  
    <bi:KpiGoal>  
        <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
    </bi:KpiGoal>  
    <bi:KpiStatus>  
        <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
    </bi:KpiStatus>  
</bi:Kpi>  
</bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

