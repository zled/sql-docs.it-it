---
title: Uso delle proprietà dei membri (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c2918188146fd84761bd23340ec5b76b48685eab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259537"
---
# <a name="using-member-properties-mdx"></a>Utilizzo delle proprietà dei membri (MDX)
  Le proprietà dei membri contengono informazioni di base su ogni membro di ogni tupla. Tali informazioni di base includono il nome del membro, il livello padre, il numero di elementi figli e così via. Le proprietà dei membri sono disponibili per tutti i membri a un livello specifico. Per quanto riguarda l'organizzazione, le proprietà dei membri vengono gestite come dati organizzati a livello di dimensione, archiviati in una singola dimensione.  
  
> [!NOTE]  
>  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]le proprietà dei membri sono dette relazioni tra attributi. Per altre informazioni, vedere [Relazioni tra attributi](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Le proprietà dei membri possono essere *intrinseche* o *personalizzate*:  
  
 Proprietà intrinseche dei membri  
 Tutti i membri supportano le proprietà intrinseche dei membri, ad esempio il valore formattato di un membro, mentre per le dimensioni e i livelli sono disponibili ulteriori proprietà intrinseche dei membri per livelli e dimensioni, quale l'ID di un membro.  
  
 Per altre informazioni, vedere [Proprietà intrinseche dei membri &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
 Proprietà dei membri definite dall'utente  
 Ai membri sono spesso associate proprietà aggiuntive. Il livello Products, ad esempio, può includere le proprietà SKU, SRP, Weight e Volume per ogni prodotto. Tali proprietà non sono membri, ma includono informazioni aggiuntive sui membri del livello Products.  
  
 Per altre informazioni, vedere [Proprietà dei membri definite dall'utente &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
 Entrambe le proprietà dei membri intrinseche e definite dall'utente può essere recuperata tramite l'utilizzo dei `PROPERTIES` parola chiave o il [proprietà](/sql/mdx/properties-mdx) (funzione).  
  
## <a name="using-the-properties-keyword"></a>Utilizzo della parola chiave PROPERTIES  
 Il `PROPERTIES` parola chiave specifica la proprietà dei membri che devono essere usate per una determinata dimensione dell'asse. Il `PROPERTIES` parola chiave viene utilizzata nell'ambito di `<axis specification>` clausola di MDX [seleziona](/sql/mdx/mdx-data-manipulation-select) istruzione:  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 La clausola `<axis_specification>` include la clausola facoltativa `<dim_props>` , come illustrato nella sintassi seguente:  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  Per altre informazioni sui valori di `<set>` e `<axis_name>`, vedere [Impostazione del contenuto di un asse della query &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 Il `<dim_props>` clausola consente di query su dimensione e a livello di proprietà dei membri usando la `PROPERTIES` (parola chiave). Il formato della clausola `<dim_props>` è illustrato nella sintassi seguente:  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Il dettaglio della sintassi di `<property>` dipende dalla proprietà su cui viene eseguita la query:  
  
-   Le proprietà dei membri intrinseche e sensibili al contesto devono essere precedute dal nome della dimensione o del livello. Le proprietà dei membri intrinseche e non sensibili al contesto non possono essere invece qualificate dal nome della dimensione o del livello. Per altre informazioni su come usare il `PROPERTIES` parola chiave con le proprietà intrinseche dei membri, vedere [proprietà intrinseche dei membri &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
-   Le proprietà dei membri definite dall'utente devono essere precedute dal nome del livello in cui si trovano. Per altre informazioni su come usare il `PROPERTIES` parola chiave con proprietà dei membri definite dall'utente, vedere [le proprietà dei membri definite dall'utente &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e utilizzo di valori della proprietà &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)  
  
  
