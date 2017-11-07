---
title: Creazione con ambito sessione set denominati (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dbfc8d3bade799db4648ee8540992ca471e7d004
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-named-sets---creating-session-scoped-named-sets"></a>Denominata set - creazione con ambito sessione MDX set denominati
  Per creare un set denominato disponibile per un'intera sessione MDX (Multidimensional Expressions), è possibile usare l'istruzione [CREATE SET](../../../mdx/mdx-data-definition-create-set.md) . Un set denominato creato utilizzando l'istruzione CREATE SET non viene rimosso fino alla chiusura della sessione MDX.  
  
 Come descritto in questo argomento, la sintassi della parola chiave WITH è intuitiva e facile da utilizzare.  
  
> [!NOTE]  
>  Per altre informazioni sui set denominati, vedere [Compilazione di set denominati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md).  
  
## <a name="create-set-syntax"></a>Sintassi di CREATE SET  
 La sintassi dell'istruzione CREATE SET è la seguente:  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 Nella sintassi di CREATE SET il parametro `cube name` contiene il nome del cubo che include i membri per il set denominato. Se il parametro `cube name` viene omesso, viene utilizzato il cubo corrente come cubo contenente il membro per il set denominato. Il parametro `Set_Identifier` contiene inoltre l'alias del set denominato e il parametro `Set_Expression` contiene l'espressione set a cui l'alias del set denominato farà riferimento.  
  
## <a name="create-set-example"></a>Esempio di CREATE SET  
 Nell'esempio seguente l'istruzione CREATE SET viene utilizzata per creare il set denominato `SetCities_2_3` basato sul cubo Store. I membri del set denominato `SetCities_2_3` sono i punti vendita presenti in City 2 e City 3.  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 Poiché è stato definito utilizzando l'istruzione CREATE SET, il set denominato `SetCities_2_3` rimane disponibile per tutta la sessione MDX corrente. Nell'esempio seguente viene illustrata una query valida che restituisce i membri di City 2 e City 3 e può essere eseguita in qualsiasi momento dopo la creazione del set denominato `SetCities_2_3` e prima della chiusura della sessione.  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di set denominati con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  

