---
title: Elemento MemberRef (CSDLBI) | Documenti Microsoft
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
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: 4
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: a90b15b4294ceaf3818fb5144bf79dae809c687a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055973"
---
# <a name="memberref-element-csdlbi"></a>Elemento MemberRef (CSDLBI)
  L'elemento MemberRef identifica il nome di una proprietà che è la destinazione di un riferimento.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento MemberRef.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|nome|Sì|Nome della proprietà contenuta in un elemento MemberRef.|  
  
## <a name="memberrefs-element"></a>Elemento MemberRefs  
 MemberRefs è un tipo complesso che definisce una raccolta di membri in cui ogni membro è contenuto in un elemento MemberRef.  
  
 Nella tabella seguente vengono elencati gli attributi e gli elementi del tipo MemberRefs.  
  
|nome|Obbligatorio|Description|  
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
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  