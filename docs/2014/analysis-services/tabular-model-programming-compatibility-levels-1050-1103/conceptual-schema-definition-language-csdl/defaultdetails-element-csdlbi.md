---
title: Elemento DefaultDetails (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa1fcc05363cf356d5895c0d5e6f62c037f45fb2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120861"
---
# <a name="defaultdetails-element-csdlbi"></a>Elemento DefaultDetails (CSDLBI)
  L'elemento DefaultDetails rappresenta un elenco di riferimenti alle proprietà che definiscono il "set di campi predefiniti" delle colonne nella tabella. Ogni proprietà può fare riferimento a una sola misura o colonna.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento DefaultDetails.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|no|Valore intero positivo che indica la presenza e la posizione nella raccolta.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene mostrato un estratto del modello di dati di esempio AdventureWorks. Esiste un solo set predefinito di colonne per la tabella Employees (titolo). Tuttavia, tre colonne sono state definite come il set di campi predefiniti per la tabella Products.  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrato un estratto della definizione della tabella Bike nel cubo Operations di Contoso. Questa annotazione indica che la colonna Color deve essere visualizzata per impostazione predefinita se non è specificata nessun'altra colonna da visualizzare.  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comprendere il modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concetti di CSDLBI](../csdlbi-concepts.md)  
  
  
