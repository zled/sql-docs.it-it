---
title: ALTER CUBE Statement (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- ALTER_CUBE
- ALTER CUBE
- ALTER
dev_langs: kbMDX
helpviewer_keywords:
- ALTER CUBE statement
- cubes [Analysis Services], modifying
- modifying cubes
ms.assetid: 2f0af61b-f509-4e1a-990f-20a215d22994
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2733f862156429fcced00fe828d709ed9440c7ac
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---alter-cube"></a>Definizione dei dati MDX - ALTER CUBE
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica la struttura di un cubo specificato, utilizzato in genere per supportare il writeback della dimensione. Per ulteriori informazioni sull'utilizzo del writeback in un'applicazione, vedere questo post di blog: [la creazione di un'applicazione di Writeback con Analysis Services (blog)](http://go.microsoft.com/fwlink/?LinkId=394977)  
  
 Si tenga presente che i writeback delle dimensioni concorrenti possono provocare un deadlock, dove il primo writeback viene bloccato da un commit a causa del blocco condiviso tenuto dal secondo writeback. In tale situazione non viene generato alcun errore ma non potrà essere eseguita alcuna operazione. Infine, viene eseguito il rollback sia del timeout che delle modifiche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER CUBE  
      Cube_Name | CURRENTCUBE  
      <alter clause>   
            [ < alter clause> ...n]  
  
< alter clause> ::=   
   <create dimension member clause>   
  | <remove dimension member clause>  
  | <move dimension member clause>   
    | <update clause>   
    | <create cell calculation clause>  
  
<create dimension member clause> ::=  
CREATE DIMENSION MEMBER [ParentName.]MemberName  
    , [[KEY = Key_Value]   
    | [Property_Name = Property_Value[, ...n]]  
  
<dropping clause>::=  
DROP   
      DIMENSION MEMBER Member_Name   
            Member_Name ...n ]   
      [WITH DESCENDANTS]  
      | [ SESSION ] [ CALCULATED ] MEMBER Member_Name   
                  [ ,Member_Name,...n ]   
    | SET Set_Name  
                  [ ,Set_Name,...n ]   
    | [ SESSION ] CELL CALCULATION CellCalc_Name  
                  [ ,CellCalc_Name,...n ]   
    | ACTION Action_Name  
  
<move dimension member clause> ::=  
MOVE DIMENSION MEMBER MemberName  
        [, SKIPPED_LEVELS = Unsigned_Integer]   
      [WITH DESCENDANTS]  
    UNDER ParentName      
  
<update clause> ::=  
UPDATE   
    CUSTOM ROLLUP FOR MEMBER MemberName  
      [,MemberName, ...n] AS MDX_Expression  
   | DIMENSION Dimension_Name | Hierarchy_Name  
      , DEFAULT_MEMBER = MDX_Expression  
   | DIMENSION MEMBER MemberName AS  
   [MDX_Expression]  
   [Property_Name = Property_Value[, ...n]]  
  
<create cell calculation clause>::=  
CELL CALCULATION Calculation_Name   
   FOR Set_Expression AS MDX_Expression   
            [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="creating-a-dimension-member"></a>Creazione di un membro in una dimensione  
 Viene aggiunta una riga alla tabella della dimensione sottostante.  
  
### <a name="arguments"></a>Argomenti  
 *ParentName*  
 Espressione stringa valida che specifica il nome del padre del nuovo membro della dimensione, a meno che questo non venga creato nella radice.  
  
 *Nome di membro*  
 Espressione stringa valida che specifica il nome di un membro.  
  
 *Key_Value*  
 Espressione scalare valida che definisce il valore chiave del nuovo membro della dimensione.  
  
 *Property_name*  
 Identificatore MDX (Multidimensional Expression) valido che rappresenta la proprietà di un membro.  
  
 *Property_Value*  
 Espressione scalare MDX (Multidimensional Expression) valida che definisce il valore della proprietà di un membro calcolato.  
  
## <a name="dropping-a-dimension-member"></a>Eliminazione di un membro in una dimensione  
 La rimozione di un membro da una dimensione abilitata per la scrittura consente di eliminare il membro e la riga corrispondente dalla tabella della dimensione sottostante.  
  
### <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che specifica il nome di un cubo.  
  
 *Member_Name*  
 Espressione stringa valida che specifica il nome o la chiave di un membro.  
  
### <a name="remarks"></a>Osservazioni  
 Se non si utilizza la clausola WITH DESCENDANTS, i figli del membro eliminato diventano figli del padre di tale membro. Se si utilizza la clausola WITH DESCENDANTS, vengono inoltre eliminati tutti i discendenti e le relative righe nella tabella della dimensione.  
  
> [!NOTE]  
>  Per informazioni sull'eliminazione di membri calcolati, set denominati, azioni e calcoli di celle, vedere [DROP MEMBER-istruzione &#40; MDX &#41; ](../mdx/mdx-data-definition-drop-member.md), [Eliminare istruzione SET &#40; MDX &#41; ](../mdx/mdx-data-definition-drop-set.md), [DROP ACTION-istruzione &#40; MDX &#41; ](../mdx/mdx-data-definition-drop-action.md), e [eliminare cella CALCULATION-istruzione &#40; MDX &#41; ](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="updating-the-default-dimension-member"></a>Aggiornamento del membro predefinito in una dimensione  
 Questa clausola consente di aggiornare il membro predefinito di un cubo e viene utilizzata nello script di calcolo MDX per definire un membro predefinito. È possibile specificare il membro predefinito per la dimensione del database, la dimensione di un cubo o l'account di accesso di un utente. È inoltre possibile cambiare il membro predefinito durante una sessione.  
  
### <a name="arguments"></a>Argomenti  
 *Dimension_Name*  
 Stringa valida che specifica il nome di una dimensione.  
  
 *MDX_Expression*  
 Espressione MDX valida che restituisce un unico membro.  
  
### <a name="remarks"></a>Osservazioni  
 L'espressione MDX specificata può essere statica o dinamica.  
  
## <a name="moving-a-dimension-member"></a>Spostamento di un membro in una dimensione  
 Nella tabella delle dimensioni sottostante viene modificata una riga.  
  
### <a name="arguments"></a>Argomenti  
 *ParentName*  
 Espressione stringa valida che specifica il nome del nuovo padre per il membro della dimensione da spostare.  
  
 *Nome di membro*  
 Espressione stringa valida che specifica il nome di un membro.  
  
 Unsigned_*Integer*  
 Numero valido che specifica il numero di livelli da ignorare.  
  
 Se si specifica la clausola WITH DESCENDANTS, viene spostata l'intero albero. Se non si specifica la clausola WITH DESCENDANTS, i figli del membro spostato diventano figli del padre di tale membro. L'effetto dello spostamento è semplicemente l'aggiornamento dei valori della colonna chiave padre nella tabella della dimensione sottostante.  
  
## <a name="updating-a-dimension-member"></a>Aggiornamento di un membro in una dimensione  
 La clausola UPDATE DIMENSION MEMBER consente di modificare le proprietà di un membro oltre alla formula personalizzata membro associata a un membro.  
  
### <a name="arguments"></a>Argomenti  
 *Nome di membro*  
 Espressione stringa valida che specifica il nome di un membro.  
  
 *MDX_Expression*  
 Espressione MDX valida che restituisce un unico membro.  
  
 *Property_Value*  
 Espressione scalare MDX valida che definisce il valore della proprietà di un membro calcolato.  
  
## <a name="creating-a-cell-calculation"></a>Creazione di una formula per il calcolo di celle  
 Per ulteriori informazioni sulla creazione di un calcolo di celle tramite l'istruzione ALTER CUBE, vedere [istruzione DROP calcolo di celle &#40; MDX &#41; ](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
