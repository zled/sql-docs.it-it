---
title: Elemento DisplayKey (CSDLBI) | Documenti Microsoft
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
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 10f388c46f9d79314107eb375aa4de6dacdf4fbf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="displaykey-element-csdlbi"></a>Elemento DisplayKey (CSDLBI)
  L'elemento DisplayKey contiene un elenco degli elementi seguenti che insieme costituiscono un identificatore sicuro. DisplayKey è presente unicamente come elemento figlio dell'elemento EntityType. Può fare riferimento a colonne o estremità del ruolo.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi dell'elemento DisplayKey.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|IsDisplayKey|No|True o false.|  
  
## <a name="remarks"></a>Osservazioni  
 Questo elemento è relativo ai report. L'elemento a cui si applica questo attributo non deve essere la chiave della tabella effettiva, solo un elemento che verrà presentato come chiave. Tuttavia la colonna utilizzata per DisplayKey deve contenere valori univoci.  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene indicata una colonna nel modello di esempio AdventureWorks che è stata specificata come DisplayKey per la tabella.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrato un estratto della rappresentazione del cubo Operations di Contoso. In questo modello, la colonna Color è stata contrassegnata come chiave di visualizzazione per la tabella Bikes.  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concetti di CSDLBI](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  

