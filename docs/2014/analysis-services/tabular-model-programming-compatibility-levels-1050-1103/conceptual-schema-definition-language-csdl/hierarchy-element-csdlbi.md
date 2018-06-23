---
title: Elemento Hierarchy (CSDLBI) | Documenti Microsoft
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
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: f2846424fdf7104c95cb4a56ac836b57583bf0cc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066772"
---
# <a name="hierarchy-element-csdlbi"></a>Elemento Hierarchy (CSDLBI)
  L'elemento Hierarchy è un contenitore logico per i campi di una tabella che è possibile collegare l'uno all'altro per formare una gerarchia. L'elemento Hierarchy è derivato dall'elemento Member di CSDL ed è stato esteso per supportare le gerarchie create in modelli di dati di Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Hierarchy.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Documentazione|no|Descrizione della gerarchia.|  
|Level|Sì|Uno o più elementi Level che definiscono le colonne utilizzate nella gerarchia.<br /><br /> Vedere [Elemento Level &#40;CSDLBI&#41;](level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Remarks  
 Nei modelli tabulari le gerarchie vengono create specificando le relazioni padre-figlio tra colonne della stessa tabella. Per altre informazioni, vedere [Gerarchie &#40;SSAS tabulare&#41;](../../tabular-models/hierarchies-ssas-tabular.md).  
  
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
 [Comprendere il modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Informazioni sulle funzioni per gerarchie padre-figlio in DAX](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [Configurare il &#40;tutti&#41; livello per le gerarchie di attributi](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  