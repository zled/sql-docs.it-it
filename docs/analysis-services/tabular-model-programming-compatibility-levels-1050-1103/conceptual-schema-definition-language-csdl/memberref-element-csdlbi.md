---
title: Elemento MemberRef (CSDLBI) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 79b6f2684dabcb45cfddac626bc2a6aa140298f3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039240"
---
# <a name="memberref-element-csdlbi"></a>Elemento MemberRef (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 **Tabulare**  
  
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
  
  
