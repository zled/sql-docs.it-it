---
title: Informazioni sull'ordine di calcolo e valutazione (MDX) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b4b865293cb9c76fb46e8fe12befb2a000d21907
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34025958"
---
# <a name="mdx-data-manipulation---understanding-pass-order-and-solve-order"></a>La modifica dei dati MDX - informazioni sulla sessione ordinamento e l'ordine di valutazione
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'operazione di calcolo di un cubo, risultante da uno script MDX, può essere suddivisa in numerose fasi di calcolo a seconda dell'utilizzo delle varie funzionalità correlate ai calcoli. Ognuna di queste fasi viene indicata come sessione di calcolo.  
  
 Per fare riferimento a una sessione di calcolo è possibile specificare una posizione ordinale, denominata numero della sessione di calcolo. Il numero di sessioni di calcolo necessario per elaborare completamente tutte le celle di un cubo è noto come livello di nidificazione della sessione di calcolo del cubo.  
  
 I dati writeback e delle tabelle dei fatti influiscono solo sulla sessione 0. Gli script popolano i dati dopo la sessione 0. Per ogni istruzione di assegnazione e calcolo in uno script viene creata una nuova sessione di calcolo. Esternamente allo script MDX, i riferimenti alla sessione assoluta 0 si riferiscono all'ultima sessione creata dallo script per il cubo.  
  
 In tutte le sessioni vengono creati membri calcolati, ma l'espressione viene applicata alla sessione corrente. Le sessioni precedenti contengono la misura calcolata, ma con un valore Null.  
  
## <a name="solve-order"></a>Ordine di valutazione  
 L'ordine di valutazione determina la priorità di calcolo in presenza di espressioni in conflitto. Nell'ambito di una singola sessione, l'ordine di valutazione determina quanto segue:  
  
-   L'ordine di valutazione applicato da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per dimensioni, membri, membri calcolati, rollup personalizzati e celle calcolate.  
  
-   L'ordine utilizzato da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per calcolare membri personalizzati, membri calcolati, rollup personalizzati e celle calcolate.  
  
 Viene data la precedenza al membro con l'ordine di valutazione più alto.  
  
> [!NOTE]  
>  L'unica eccezione è rappresentata dalla funzione di aggregazione. Per i membri calcolati con la funzione di aggregazione viene applicato un ordine di valutazione inferiore rispetto a qualsiasi misura calcolata intersecante.  
  
## <a name="solve-order-values-and-precedence"></a>Valori dell'ordine di valutazione e precedenze  
 I valori dell'ordine di valutazione sono compresi tra -8181 e 65535. In questo intervallo, alcuni valori dell'ordine di valutazione corrispondono a tipi specifici di calcoli, come illustrato nella tabella seguente.  
  
|Calcolo|Ordine di valutazione|  
|-----------------|-----------------|  
|Formule personalizzate membro|-5119|  
|Operatori unari|-5119|  
|Calcolo di totali visualizzati|-4096|  
|Tutti gli altri calcoli (se non diversamente specificato)|0|  
  
 È consigliabile utilizzare esclusivamente numeri interi positivi per l'impostazione dei valori dell'ordine di valutazione. Se si assegnano valori inferiori a quelli indicati nella tabella precedente, il risultato della sessione di calcolo può diventare imprevedibile. Se, ad esempio, al calcolo per un membro calcolato viene assegnato un valore dell'ordine di valutazione inferiore al valore predefinito delle formule di rollup personalizzato, che corrisponde a -5119, tale valore comporta l'esecuzione del calcolo dei membri calcolati prima delle formule di rollup personalizzato e può produrre risultati non corretti.  
  
### <a name="creating-and-changing-solve-order"></a>Creazione e modifica dell'ordine di valutazione  
 Nel **riquadro Calcoli**di Progettazione cubi è possibile modificare l'ordine di valutazione per i membri calcolati e le celle calcolate modificando l'ordine dei calcoli.  
  
 In MDX è possibile usare la parola chiave **SOLVE_ORDER** per creare o modificare l'ordine di valutazione per membri calcolati e celle calcolate.  
  
## <a name="solve-order-examples"></a>Esempi di ordine di valutazione  
 Per illustrare le potenziali complessità correlate all'ordine di valutazione, la serie seguente di query MDX inizia con due query che singolarmente non presentano problemi a livello di ordine di valutazione. Queste due query vengono quindi combinate in una singola query, che richiede l'applicazione dell'ordine di valutazione.  
  
> [!NOTE]  
>  È possibile eseguire queste query MDX sul database multidimensionale di esempio Adventure Works. È possibile scaricare l'esempio relativo ai [modelli multidimensionali di AdventureWorks per SQL Server 2012](http://msftdbprodsamples.codeplex.com/releases/view/55330) dal sito codeplex.  
  
### <a name="query-1differences-in-income-and-expenses"></a>Query 1 - Differenze tra reddito e spese  
 Per la prima query MDX, calcolare la differenza tra vendite e costi per ogni anno costruendo una semplice query MDX simile all'esempio seguente:  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] )  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 In questa query è presente un solo membro calcolato, cioè `Year Difference`. Essendo presente un solo membro calcolato, l'ordine di valutazione è irrilevante, a condizione che nel cubo non vengano utilizzati membri calcolati.  
  
 Questa query MDX genera un set di risultati simile a quello illustrato nella tabella seguente.  
  
||Importo vendite Internet|Internet Total Product Cost|  
|-|---------------------------|---------------------------------|  
|**CY 2007**|$9,791,060.30|$5,718,327.17|  
|**CY 2008**|$9,770,899.74|$5,721,205.24|  
|**Year Difference**|($20,160.56)|$2,878.06|  
  
### <a name="query-2percentage-of-income-after-expenses"></a>Query 2 - Percentuale di reddito al netto delle spese  
 Per la seconda query, calcolare la percentuale di reddito al netto delle spese per ogni anno utilizzando la query MDX seguente:  
  
```  
WITH   
MEMBER  
[Measures].[Profit Margin] AS   
([Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent"  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 In questa query MDX, come nella precedente, è presente un solo membro calcolato, `Profit Margin`, e pertanto non presenta complicazioni relativamente all'ordine di valutazione.  
  
 Questa query MDX genera un set di risultati leggermente diverso, simile a quello illustrato nella tabella seguente.  
  
||Importo vendite Internet|Internet Total Product Cost|Profit Margin|  
|-|---------------------------|---------------------------------|-------------------|  
|**CY 2007**|$9,791,060.30|$5,718,327.17|41.60%|  
|**CY 2008**|$9,770,899.74|$5,721,205.24|41.45%|  
  
 Le differenze nei set di risultati della prima e della seconda query sono dovute alla diversa posizione del membro calcolato. Nella prima query il membro calcolato fa parte dell'asse ROWS e non dell'asse COLUMNS indicato nella seconda query. Questa differenza di posizione diventa importante nella query successiva, in cui i due membri calcolati vengono combinati in una singola query MDX.  
  
### <a name="query-3combined-year-difference-and-net-income-calculations"></a>Query 3 - Calcolo combinato della differenza annuale e del reddito netto  
 Nella query finale, in cui vengono combinati entrambi gli esempi precedenti in una singola query MDX, l'ordine di valutazione diventa importante a causa dei calcoli in entrambe le colonne e le righe. Per assicurarsi che i calcoli vengano eseguiti nella sequenza corretta, definire la sequenza di esecuzione dei calcoli tramite la parola chiave **SOLVE_ORDER** .  
  
 La parola chiave **SOLVE_ORDER** consente di specificare l'ordine di valutazione dei membri calcolati in una query MDX o in un comando **CREATE MEMBER** . I valori integer utilizzati con la parola chiave **SOLVE_ORDER** sono relativi e non devono necessariamente iniziare da zero o essere consecutivi. Il valore indica semplicemente al sistema MDX di calcolare un membro in base ai valori derivati dal calcolo dei membri con un valore superiore. Se un membro calcolato viene definito senza la parola chiave **SOLVE_ORDER** , il relativo valore predefinito sarà zero.  
  
 Se ad esempio si combinano i calcoli utilizzati nelle prime due query di esempio, i due membri calcolati `Year Difference` e `Profit Margin`si intersecano in corrispondenza di una singola cella nel set di dati risultante dell'esempio di query MDX. L'unico modo per determinare come questa cella verrà valutata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] consiste nell'usare l'ordine di valutazione. Le formule utilizzate per creare la cella genereranno risultati diversi a seconda dell'ordine di valutazione dei due membri calcolati.  
  
 Provare innanzitutto a combinare nella query MDX seguente i calcoli utilizzati nelle prime due query:  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 1  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 2  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 In questo esempio di query MDX combinata, a `Profit Margin` è associato l'ordine di valutazione più alto, pertanto ha la precedenza quando le due espressioni interagiscono. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] valuta la cella in questione tramite la formula `Profit Margin`. Nella tabella seguente sono riportati i risultati di questo calcolo nidificato.  
  
||Importo vendite Internet|Internet Total Product Cost|Profit Margin|  
|-|---------------------------|---------------------------------|-------------------|  
|**CY 2007**|$9,791,060.30|$5,718,327.17|41.60%|  
|**CY 2008**|$9,770,899.74|$5,721,205.24|41.45%|  
|**Year Difference**|($20,160.56)|$2,878.06|114.28%|  
  
 Il risultato nella cella condivisa è basato sulla formula per `Profit Margin`. Ciò significa che in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene calcolato il risultato nella cella condivisa con i dati di `Year Difference` , generando la formula seguente (il risultato è arrotondato per maggiore chiarezza):  
  
```  
((9,770,899.74 - 9,791,060.30) - (5,721,205.24 - 5,718,327.17)) / (9,770,899.74 - 9,791,060.30) = 1.14275744   
```  
  
 Oppure  
  
```  
(23,038.63) / (20,160.56) = 114.28%  
```  
  
 È chiaramente errata. Il risultato nella cella condivisa viene tuttavia calcolato diversamente in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] se si cambiano gli ordini di valutazione per i membri calcolati nella query MDX. Nella query MDX combinata seguente viene invertito l'ordine di valutazione dei membri calcolati:  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 2  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 1  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 Poiché l'ordine dei membri calcolati è stato cambiato, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene usate la formula `Year Difference` per valutare la cella, come illustrato nella tabella seguente.  
  
||Importo vendite Internet|Internet Total Product Cost|Profit Margin|  
|-|---------------------------|---------------------------------|-------------------|  
|**CY 2007**|$9,791,060.30|$5,718,327.17|41.60%|  
|**CY 2008**|$9,770,899.74|$5,721,205.24|41.45%|  
|**Year Difference**|($20,160.56)|$2,878.06|(0.15%)|  
  
 Poiché nella query viene usata la formula `Year Difference` con i dati `Profit Margin` , la formula per la cella condivisa assomiglia al calcolo seguente:  
  
```  
(($9,770,899.74 - 5,721,205.24) / $9,770,899.74) - ((9,791,060.30 - 5,718,327.17) / 9,791,060.30) = -0.15   
```  
  
 Oppure  
  
```  
0.4145 - 0.4160= -0.15  
```  
  
## <a name="additional-considerations"></a>Ulteriori considerazioni  
 L'ordine di valutazione può essere un aspetto estremamente complesso da affrontare, soprattutto in cubi con un numero elevato di dimensioni che includono membri calcolati, formule di rollup personalizzato o celle calcolate. Quando in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene valutata una query MDX, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prende in considerazione i valori dell'ordine di valutazione per tutti gli elementi coinvolti in una determinata sessione, incluse le dimensioni del cubo specificate nella query MDX.  
  
## <a name="see-also"></a>Vedere anche  
 [CalculationCurrentPass & #40; MDX & #41;](../../../mdx/calculationcurrentpass-mdx.md)   
 [CalculationPassValue & #40; MDX & #41;](../../../mdx/calculationpassvalue-mdx.md)   
 [CREARE l'istruzione MEMBER & #40; MDX & #41;](../../../mdx/mdx-data-definition-create-member.md)   
 [La modifica di dati & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  
