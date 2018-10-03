---
title: Elemento KPI (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 09f42856788dffa45a03690c87e2383849c5f813
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189821"
---
# <a name="kpi-element-csdlbi"></a>Elemento KPI (CSDLBI)
  L'elemento KPI definisce un calcolo che può essere utilizzato come indicatore di prestazioni di chiave. In un modello di dati di Business Intelligence, gli indicatori KPI sono basati sulle misure e per questo la relativa definizione contiene tutti i metadati associati alle misure, nonché le informazioni necessarie per la presentazione dei valori KPI, incluso un grafico predefinito.  
  
 L'elemento KPI non specifica la formula, contenuta nella definizione della misura, ma i metadati aggiuntivi associati alle misure utilizzate come indicatori di prestazioni chiave. Dopo avere definito una misura come KPI, non è più possibile utilizzarla come misura in altri contesti.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento KPI.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Documentazione|no|Descrizione dell'indicatore KPI.|  
|KpiGoal|Sì|Riferimento a una colonna contenente valori che possono essere utilizzati come obiettivo.<br /><br /> Vedere [Elemento PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)a.|  
|KpiStatus|Sì|Riferimento a una colonna contenente valori che rappresentano lo stato corrente dell'indicatore KPI.|  
|StatusGraphic|Sì|Riferimento a un'immagine che indica lo stato negativo, positivo o neutro rispetto agli obiettivi definiti nell'elemento KPI.|  
  
## <a name="remarks"></a>Note  
 Quando si progetta un modello, è possibile creare un indicatore KPI creando una misura e destinandola all'utilizzo come indicatore KPI. È quindi necessario aggiungere le informazioni specifiche degli indicatori di prestazione chiave, ad esempio un grafico per mostrare le tendenze.  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
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
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
