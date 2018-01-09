---
title: Creazione con ambito sessione calcolato membri (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 273553132fd9a3cd32900fef28800d28c9f6c1d5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-calculated-members---session-scoped-calculated-members"></a>Membri: membri calcolati con ambito sessione di calcolo MDX
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Per creare un membro calcolato è disponibile per tutta una sessione MDX (Multidimensional Expressions), utilizzare il [CREATE MEMBER](../../../mdx/mdx-data-definition-create-member.md) istruzione. Un membro calcolato creato utilizzando l'istruzione CREATE MEMBER non viene rimosso fino alla chiusura della sessione MDX.  
  
 Come descritto in questo argomento, la sintassi dell'istruzione CREATE MEMBER è intuitiva e facile da utilizzare.  
  
> [!NOTE]  
>  Per altre informazioni sui membri calcolati, vedere [Compilazione di membri calcolati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="create-member-syntax"></a>Sintassi dell'istruzione CREATE MEMBER  
 Per aggiungere l'istruzione CREATE MEMBER a un'istruzione MDX, utilizzare la sintassi seguente:  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 Nella sintassi dell'istruzione CREATE MEMBER il valore `fully-qualified-member-name` rappresenta il nome completo del membro calcolato. Il nome completo include la dimensione o il livello a cui è associato il membro calcolato. Il valore `expression` restituisce il valore del membro calcolato dopo la valutazione del valore dell'espressione.  
  
## <a name="create-member-example"></a>Esempio sull'istruzione CREATE MEMBER  
 Nell'esempio seguente l'istruzione CREATE MEMBER viene utilizzata per creare il membro calcolato `LastFourStores` , che restituisce la somma delle unità vendute negli ultimi quattro punti vendita e sarà disponibile per l'intera sessione del cubo.  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di membri calcolati con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
