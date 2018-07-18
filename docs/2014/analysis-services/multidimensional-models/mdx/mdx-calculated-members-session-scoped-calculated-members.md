---
title: Creazione con ambito sessione calcolato membri (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d8e51a2fa5d8179134ac2654f55e9da7ff5ced67
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063724"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a>Creazione di membri calcolati con ambito sessione (MDX)
  Per creare un membro calcolato disponibile nell'ambito di un'intera sessione MDX (Multidimensional Expressions), è possibile usare l'istruzione [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member). Un membro calcolato creato utilizzando l'istruzione CREATE MEMBER non viene rimosso fino alla chiusura della sessione MDX.  
  
 Come descritto in questo argomento, la sintassi dell'istruzione CREATE MEMBER è intuitiva e facile da utilizzare.  
  
> [!NOTE]  
>  Per altre informazioni sui membri calcolati, vedere [Compilazione di membri calcolati in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
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
 [Creazione di Query con ambito di membri calcolati &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  