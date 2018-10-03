---
title: Elemento DisplayKey (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 929529214979c2c8bd6c441914ef84974a86a807
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060031"
---
# <a name="displaykey-element-csdlbi"></a>Elemento DisplayKey (CSDLBI)
  L'elemento DisplayKey contiene un elenco degli elementi seguenti che insieme costituiscono un identificatore sicuro. DisplayKey è presente unicamente come elemento figlio dell'elemento EntityType. Può fare riferimento a colonne o estremità del ruolo.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi dell'elemento DisplayKey.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|IsDisplayKey|no|True o false.|  
  
## <a name="remarks"></a>Note  
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
 [Comprendere il modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concetti di CSDLBI](../csdlbi-concepts.md)  
  
  
