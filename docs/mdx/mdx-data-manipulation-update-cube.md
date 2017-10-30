---
title: Istruzione UPDATE CUBE (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- UPDATE CUBE
- UPDATE_CUBE
- UPDATE
dev_langs:
- kbMDX
helpviewer_keywords:
- updating cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
ms.assetid: 6c8f23bb-401b-49de-843a-5324ac977239
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0be79c064b4c4f7044b495056295420094aa13e8
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-manipulation---update-cube"></a>Manipolazione dei dati MDX - UPDATE CUBE
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'istruzione UPDATE CUBE viene utilizzata per eseguire il writeback dei dati in qualsiasi cella di un cubo aggregato al relativo elemento padre mediante l'aggregazione SUM. Per ulteriori informazioni ed esempi, vedere "Informazioni sulle allocazioni" in questo post di blog: [la creazione di un'applicazione di Writeback con Analysis Services (blog)](http://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Stringa valida che specifica il nome di un cubo.  
  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
 *Nuovo_valore*  
 Espressione numerica valida.  
  
 *Weight_Expression*  
 Espressione numerica MDX (Multidimensional Expression) valida che restituisce un valore decimale compreso tra 0 e 1.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile aggiornare il valore di una cella foglia o non foglia specificata di un cubo, allocando facoltativamente il valore di una cella non foglia specificata a celle foglia dipendenti. La cella specificata dall'espressione di tupla può essere una cella valida qualsiasi dello spazio multidimensionale, ovvero la cella non deve essere necessariamente una cella foglia. Tuttavia, la cella deve essere aggregata con la [somma](../mdx/sum-mdx.md) funzione di aggregazione e non deve includere un membro calcolato nella tupla utilizzata per identificare la cella.  
  
 Potrebbe essere opportuno considerare il **UPDATE CUBE** istruzione come una subroutine che genera automaticamente una serie di operazioni di writeback delle celle singole celle foglia e non foglia che eseguirà il rollup somma specificata.  
  
 Di seguito è una descrizione dei metodi di allocazione.  
  
 **USE_EQUAL_ALLOCATION:** ogni cella foglia che contribuisce alla cella aggiornata verrà assegnato un valore uguale basato sull'espressione seguente.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:**ogni cella foglia che contribuisce alla cella aggiornata verrà modificato in base all'espressione seguente.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:** ogni cella foglia che contribuisce alla cella aggiornata verrà assegnato un valore uguale è basato sull'espressione seguente.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:** ogni cella foglia che contribuisce alla cella aggiornata verrà modificato in base all'espressione seguente.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Se un'espressione di ponderazione non è specificata, il **UPDATE CUBE** istruzione utilizza in modo implicito l'espressione seguente.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Un'espressione di ponderazione deve essere espressa come valore decimale compreso tra zero (0) e 1. Questo valore specifica il rapporto del valore allocato che si desidera assegnare alle celle foglia interessate dall'allocazione. È responsabilità dello sviluppatore dell'applicazione client creare espressioni con valori aggregati di rollup uguali ai valori allocati dalle espressioni.  
  
> [!CAUTION]  
>  L'applicazione client deve prendere in considerazione l'allocazione di tutte le dimensioni simultaneamente in modo da evitare risultati imprevisti, tra cui valori di rollup non corretti o dati inconsistenti.  
  
 Ogni **UPDATE CUBE** allocazione deve essere considerata atomica fini delle transazioni. Ciò significa che, se una delle operazioni di allocazione ha esito negativo, ad esempio nel caso di errore in una formula o di una violazione di sicurezza, l'intera operazione UPDATE CUBE avrà esito negativo. Prima dell'elaborazione dei calcoli delle singole operazioni di allocazione viene eseguito uno snapshot dei dati per assicurare che i calcoli risultanti siano corretti.  
  
> [!CAUTION]  
>  Quando si utilizza una misura contenente dati integer, il metodo USE_WEIGHTED_ALLOCATION potrebbe restituire risultati non precisi in seguito a modifiche di arrotondamento incrementali.  
  
> [!IMPORTANT]  
>  Quando le celle aggiornate non si sovrappongono, la proprietà della stringa di connessione **Update Isolation Level** può essere usata per migliorare le prestazioni di UPDATE CUBE.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Le istruzioni di manipolazione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  

