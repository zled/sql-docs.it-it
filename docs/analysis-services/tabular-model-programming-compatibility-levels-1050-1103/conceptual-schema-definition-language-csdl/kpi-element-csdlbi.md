---
title: Elemento KPI (CSDLBI) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc368aed1186c20e76ce643a33673030713547ba
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34041333"
---
# <a name="kpi-element-csdlbi"></a>Elemento KPI (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'elemento KPI definisce un calcolo che può essere utilizzato come indicatore di prestazioni di chiave. In un modello di dati di Business Intelligence, gli indicatori KPI sono basati sulle misure e per questo la relativa definizione contiene tutti i metadati associati alle misure, nonché le informazioni necessarie per la presentazione dei valori KPI, incluso un grafico predefinito.  
  
 L'elemento KPI non specifica la formula, contenuta nella definizione della misura, ma i metadati aggiuntivi associati alle misure utilizzate come indicatori di prestazioni chiave. Dopo avere definito una misura come KPI, non è più possibile utilizzarla come misura in altri contesti.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento KPI.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Documentazione|No|Descrizione dell'indicatore KPI.|  
|KpiGoal|Sì|Riferimento a una colonna contenente valori che possono essere utilizzati come obiettivo.<br /><br /> Vedere [Elemento PropertyRef &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md)a.|  
|KpiStatus|Sì|Riferimento a una colonna contenente valori che rappresentano lo stato corrente dell'indicatore KPI.|  
|StatusGraphic|Sì|Riferimento a un'immagine che indica lo stato negativo, positivo o neutro rispetto agli obiettivi definiti nell'elemento KPI.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando si progetta un modello, è possibile creare un indicatore KPI creando una misura e destinandola all'utilizzo come indicatore KPI. È quindi necessario aggiungere le informazioni specifiche degli indicatori di prestazione chiave, ad esempio un grafico per mostrare le tendenze.  
  
## <a name="example"></a>Esempio  
 **Tabulare**  
  
 Nell'esempio seguente, in CSDLBI versione 1.0, viene riportato un indicatore KPI che misura le vendite, dal modello tabulare di esempio di AdventureWorks.  
  
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
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato un indicatore KPI del cubo Operations di Contoso.  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
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
  
  
