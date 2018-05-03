---
title: Funzioni (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- DMX [Analysis Services], functions
- VBA [DMX]
- stored procedures [DMX]
- functions [DMX]
- Excel [DMX]
- Data Mining Extensions [Analysis Services], functions
ms.assetid: 75ab6346-f4a4-4699-90f3-66d35f930ed7
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ba4f13bed63954643e6678ca4210400cb91c3b98
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="functions-dmx"></a>Funzioni (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Quando si utilizza estensioni DMX (Data Mining) per gli oggetti query [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], è possibile utilizzare funzioni per ottenere altre informazioni oltre ai valori delle colonne nel modello di data mining o set di dati input. È ad esempio possibile utilizzare query DMX per ottenere sia il valore stimato di una colonna, sia la probabilità che tale stima sia corretta. Oltre alle funzioni DMX è possibile utilizzare anche stored procedure e funzioni di Microsoft Visual Basic, Applications Edition (VBA) e Microsoft Excel.  
  
## <a name="dmx-functions"></a>Funzioni DMX  
 È possibile utilizzare funzioni DMX per eseguire le attività seguenti:  
  
-   Restituire stime.  
  
-   Restituire statistiche relative a una stima, quali probabilità e supporto.  
  
-   Filtrare i risultati di una query.  
  
-   Riordinare un'espressione di tabella.  
  
 La maggior parte delle funzioni DMX restituisce un valore scalare, ad esempio il supporto di una stima, ma alcune restituiscono un risultato tabulare. Ad esempio, la funzione PredictHistogram restituisce una tabella che contiene il supporto e probabilità per ogni stato della colonna stimabile specificata. I risultati vengono visualizzati come una nuova colonna di tabella.  
  
 **Per ulteriori informazioni:** [le funzioni di stima generali &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md), [estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
## <a name="visual-basic-for-applications-vba-and-excel-functions"></a>Funzioni di Visual Basic, Applications Edition (VBA) e di Excel  
 Oltre alle funzioni DMX, dalle istruzioni DMX è possibile chiamare anche un'ampia gamma di funzioni di Excel e VBA. Ad esempio, è possibile utilizzare la funzione lCase per modificare la modalità di visualizzazione della colonna Attribute_Name nel contenuto del modello TM_Decision_Tree. come illustrato nell'esempio di codice seguente.  
  
```  
SELECT lCase([Attribute_Name])   
FROM [TM_Decision_Tree].CONTENT  
```  
  
 Se la stessa funzione esiste in Excel e VBA, è necessario anteporre il nome della funzione nell'istruzione DMX con **VBA** o **Excel**. specificando ad esempio `VBA!Log` o `Excel!Log`. Se la funzione di Excel o VBA da utilizzare esiste anche in DMX o MDX (Multidimensional Expressions), oppure contiene un simbolo di dollaro ($), sarà necessario utilizzare le parentesi quadre ([]) come caratteri di escape. Per chiamare la funzione può essere ad esempio necessario specificare `[VBA!Format]`.  
  
## <a name="stored-procedures"></a>Stored procedure  
 È possibile utilizzare linguaggi di programmazione CLR (Common Language Runtime) per creare stored procedure in grado di estendere le funzionalità di DMX. Ad esempio, un modello di data mining dell'albero di regressione restituisce coefficienti, ad esempio A, B e così via, che descrivono l'equazione di regressione, ma il modello non viene restituito l'equazione, ad esempio A + Bx = y. È tuttavia possibile creare una stored procedure che utilizza l'oggetto modello di data mining per navigare nello schema del contenuto e restituire l'equazione di regressione come output. Un'istruzione DMX può pertanto restituire un elenco di equazioni di regressione nell'ambito dei risultati di una query.  
  
 **Per ulteriori informazioni:** [gestione di assembly di modello multidimensionale](../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions & #40; DMX & #41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
