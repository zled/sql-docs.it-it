---
title: Elemento Hierarchy (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
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
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f3ff3c0bd93b75384b53e1f386a14196bcc803c3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchy-element-csdlbi"></a>Elemento Hierarchy (CSDLBI)
  L'elemento Hierarchy è un contenitore logico per i campi di una tabella che è possibile collegare l'uno all'altro per formare una gerarchia. L'elemento Hierarchy è derivato dall'elemento Member di CSDL ed è stato esteso per supportare le gerarchie create in modelli di dati di Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Hierarchy.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Documentazione|No|Descrizione della gerarchia.|  
|Level|Sì|Uno o più elementi Level che definiscono le colonne utilizzate nella gerarchia.<br /><br /> Vedere [Elemento Level &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Osservazioni  
 Nei modelli tabulari le gerarchie vengono create specificando le relazioni padre-figlio tra colonne della stessa tabella. Per altre informazioni, vedere [Gerarchie &#40;SSAS tabulare&#41;](../../../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.0, viene illustrata una gerarchia del modello di esempio AdventureWorks che è stata aggiunta alla tabella Products.  
  
```  
  
<bi:Hierarchy Name="Categoryy">  
    <bi:Level Name="CategoryName">  
       <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
       </bi:Source>  
    </bi:Level>  
    <bi:Level Name="ProductName">  
       <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
       </bi:Source>  
    </bi:Level>  
</bi:Hierarchy>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato una gerarchia del cubo Operations di Contoso Retail.  
  
```  
  
<bi:Hierarchy Name="Product_Hierarchy" Caption="Product Hierarchy" ReferenceName="Product Hierarchy">  
   <bi:Documentation>  
      <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
   </bi:Documentation>  
  
   <bi:Level Name="ProductLine">  
      <bi:Source>  
      <bi:PropertyRef Name="ProductLine" />  
      </bi:Source>  
   </bi:Level>  
  
   <bi:Level Name="ModelName">  
         <bi:Source>  
      <bi:PropertyRef Name="ModelName" />  
      </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Informazioni sulle funzioni per gerarchie padre-figlio in DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Configurare il &#40; Tutti i &#41; Livello per le gerarchie di attributi](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  

