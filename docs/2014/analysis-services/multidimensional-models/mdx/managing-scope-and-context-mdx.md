---
title: Gestione di ambito e contesto (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5bcaff42dd71f1c278c390d06240657f5f80f112
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118111"
---
# <a name="managing-scope-and-context-mdx"></a>Gestione di ambito e contesto (MDX)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]uno script MDX (Multidimensional Expressions) può essere applicato all'intero cubo o a determinate parti del cubo, in punti specifici dell'esecuzione dello script. Uno script MDX può utilizzare un approccio a livelli per i calcoli all'interno di un cubo, tramite l'utilizzo di sessioni di calcolo.  
  
> [!NOTE]  
>  Per altre informazioni sull'effetto delle sessioni di calcolo sui calcoli, vedere [Informazioni sull'ordine di calcolo e di valutazione &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 Per controllare la sessione di calcolo, ambito e contesto all'interno di uno script MDX, in particolare usare l'istruzione Calculate, la `This` (funzione) e l'istruzione SCOPE.  
  
## <a name="using-the-calculate-statement"></a>Utilizzo dell'istruzione CALCULATE  
 L'istruzione CALCULATE popola ogni cella del cubo con dati aggregati. Lo script MDX predefinito, ad esempio, include una sola istruzione CALCULATE all'inizio dello script.  
  
 Per altre informazioni sulla sintassi dell'istruzione CALCULATE, vedere [Istruzione CALCULATE &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate).  
  
> [!NOTE]  
>  Se lo script include un'istruzione SCOPE che contiene un'istruzione CALCULATE, MDX valuterà l'istruzione CALCULATE nel contesto del sottocubo definito dall'istruzione SCOPE, non rispetto all'intero cubo.  
  
## <a name="using-the-this-function"></a>Utilizzo della funzione This  
 La funzione `This` consente di recuperare il sottocubo corrente in uno script MDX. È possibile usare il `This` funzione per impostare rapidamente su un'espressione MDX il valore delle celle del sottocubo corrente. Usano spesso il `This` funzione unitamente all'istruzione SCOPE per modificare il contenuto di uno specifico sottocubo durante una sessione di calcolo specifico.  
  
> [!NOTE]  
>  Se lo script include un'istruzione SCOPE che contiene un `This` funzione, MDX valuterà la `This` funzione all'interno del contesto del sottocubo definito dall'istruzione SCOPE, non rispetto all'intero cubo.  
  
### <a name="this-function-example"></a>Esempio di funzione This  
 L'esempio di comando di script MDX seguente usa il `This` funzione per aumentare il valore della misura Amount, nel gruppo di misure Finance del [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] cubo di esempio, 10% per i bambini del membro Redmond della dimensione Customer:  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Per altre informazioni sulla sintassi della `This` funzione, vedere [questo &#40;MDX&#41;](/sql/mdx/this-mdx).  
  
## <a name="using-the-scope-statement"></a>Utilizzo dell'istruzione SCOPE  
 L'istruzione SCOPE definisce il sottocubo corrente che contiene e specifica l'ambito di altre espressioni e istruzioni MDX dello script MDX. MDX valuta tali espressioni e istruzioni MDX aggiuntive, comprese la funzione `This` e l'istruzione CALCULATE, nel contesto del sottocubo.  
  
 Un'istruzione SCOPE è dinamica, ma non iterativa. Le istruzioni contenute in un'istruzione SCOPE vengono eseguite una volta sola, ma il sottocubo può essere determinato dinamicamente. Si consideri ad esempio un cubo di nome SampleCube. A tale cubo viene applicata l'istruzione SCOPE seguente, per creare un sottocubo che definisce come contesto il risultato della funzione ALLMEMBERS applicata alla dimensione Measures:  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 Le istruzioni e le espressioni contenute in questa istruzione SCOPE vengono eseguite una volta sola.  
  
 Si supponga ora che un utente aziendale esegua la query MDX seguente, che contiene una sola misura di nome ExistingMeasure, sul cubo SampleCube:  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 Il set di celle restituito dalla query è simile all'output illustrato nella tabella seguente.  
  
||[ExistingMeasure]|[NewMeasure]|  
|-|-------------------------|--------------------|  
|[Customer].[All]|2|2|  
  
 Osservando il set di celle restituito, è possibile notare che il valore ExistingMeasure incluso nell'istruzione SCOPE dello script MDX viene aggiornato dinamicamente dopo la definizione della misura NewMeasure.  
  
 Un'istruzione SCOPE può essere nidificata in un'altra istruzione SCOPE. Poiché l'istruzione SCOPE non è iterativa, la nidificazione delle istruzioni SCOPE viene utilizzata principalmente per suddividere ulteriormente un sottocubo per scopi particolari.  
  
### <a name="scope-statement-example"></a>Esempio di istruzione SCOPE  
 Nell'esempio di script MDX seguente l'istruzione SCOPE viene utilizzata per incrementare del 10% il valore della misura Amount, nel gruppo di misure Finance del cubo di esempio [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] , per i bambini del membro Redmond della dimensione Customer. Un'altra istruzione SCOPE modifica tuttavia il sottocubo in modo da includere la misura Amount per i bambini dell'anno di calendario 2002. La misura Amount viene infine aggregata solo per tale sottocubo, mentre i valori aggregati per la misura Amount relativa agli altri anni di calendario restano invariati.  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Per altre informazioni sulla sintassi dell'istruzione SCOPE, vedere [Istruzione SCOPE &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al linguaggio MDX &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Script MDX di base &#40;MDX&#41;](the-basic-mdx-script-mdx.md)   
 [Nozioni fondamentali sulle Query MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
