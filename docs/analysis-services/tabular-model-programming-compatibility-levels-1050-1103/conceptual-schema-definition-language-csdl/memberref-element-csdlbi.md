---
title: Elemento MemberRef (CSDLBI) | Documenti Microsoft
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
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ca4fcb2b59e2a99153ccd55fce93be47a58d961
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="memberref-element-csdlbi"></a>Elemento MemberRef (CSDLBI)
  L'elemento MemberRef identifica il nome di una proprietà che è la destinazione di un riferimento.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento MemberRef.  
  
|Nome|Obbligatorio|Descrizione|  
|----------|-----------------|-----------------|  
|Nome|Sì|Nome della proprietà contenuta in un elemento MemberRef.|  
  
## <a name="memberrefs-element"></a>Elemento MemberRefs  
 MemberRefs è un tipo complesso che definisce una raccolta di membri in cui ogni membro è contenuto in un elemento MemberRef.  
  
 Nella tabella seguente vengono elencati gli attributi e gli elementi del tipo MemberRefs.  
  
|Nome|Obbligatorio|Descrizione|  
|----------|-----------------|-----------------|  
|MemberRef|Sì|Stringa contenente il riferimento al membro.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene rappresentata una parte del modello di esempio AdventureWorks che definisce la tabella Products. L'elemento MemberRef viene utilizzato per ogni colonna inclusa nel set di campi predefinito per il modello.  
  
```  
  
<bi:EntityType>  
   <bi:DefaultDetails>  
     <bi:MemberRef Name="Color" />  
     <bi:MemberRef Name="DealerPrice" />  
     <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene rappresentata una parte del cubo Operations di Contoso che definisce la tabella Bikes. In questo esempio, viene utilizzato un elemento MemberRef per specificare il nome della colonna usata come set di campi predefinito nei report e un altro elemento MemberRef per fare riferimento alla colonna che fornisce il tipo di ordinamento.  
  
```  
  
<bi:DefaultDetails>  
   <bi:MemberRef Name="Color" />  
</bi:DefaultDetails>  
  
<bi:SortMembers>  
   <bi:MemberRef Name="Color" />  
</bi:SortMembers>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

