---
title: Utilizzo della funzione RollupChildren (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1c913406650e267cb715267f4a2a91235b6259b4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-data-manipulation---rollupchildren-function"></a>Manipolazione dei dati MDX - funzione RollupChildren
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Le espressioni MDX (Multidimensional) [RollupChildren](../../../mdx/rollupchildren-mdx.md) funzione rollup degli elementi figlio di un membro, applicando un operatore unario diverso per ogni elemento figlio e restituisce il valore di tale rollup sotto forma di numero. L'operatore unario utilizzato può essere specificato da una proprietà del membro associata al membro figlio oppure può essere costituito da un'espressione stringa fornita direttamente alla funzione.  
  
## <a name="rollupchildren-function-examples"></a>Esempi sulla funzione RollupChildren  
 L'uso della funzione **RollupChildren** nelle istruzioni MDX (Multidimensional Expressions) è semplice da spiegare, ma questa funzione può avere un'ampia gamma di effetti sulle query MDX.  
  
 L'effetto della funzione **RollupChildren** viene rilevato nelle query MDX progettate per l'esecuzione dell'analisi selettiva sui dati di un cubo esistenti. Nella tabella seguente è riportato, ad esempio, un elenco di membri figlio per il membro padre Net Sales, con i relativi operatori unari (rappresentati dalla proprietà **UNARY_OPERATOR** del membro) indicati tra parentesi.  
  
|Membro padre|Membro figlio|  
|-------------------|------------------|  
|Net Sales|Domestic Sales (+)<br /><br /> Domestic Returns (-)<br /><br /> Foreign Sales (+)<br /><br /> Foreign Returns (-)|  
  
 Il membro padre Net Sales specifica le vendite nette totali meno i valori delle vendite nazionali ed estere lorde, sottraendo i resi nazionali ed esteri durante il rollup.  
  
 Si desidera tuttavia fornire una previsione semplice e rapida delle vendite lorde nazionali ed estere maggiorata del 10%, ignorando i resi nazionali ed esteri. Per calcolare tale valore, è possibile usare la funzione **RollupChildren** in uno dei due modi seguenti: con una proprietà personalizzata del membro o con la funzione **IIf** .  
  
### <a name="using-a-custom-member-property"></a>Utilizzo di una proprietà personalizzata del membro  
 Se il calcolo del rollup deve essere eseguito di frequente, è consigliabile creare una proprietà di membro in cui memorizzare l'operatore da utilizzare per ogni membro figlio per una funzione specifica. Nella tabella seguente sono indicati gli operatori unari validi e vengono descritti i risultati previsti.  
  
|Operatore|Risultato|  
|--------------|------------|  
|+|totale = totale + membro figlio corrente|  
|-|totale = totale - membro figlio corrente|  
|*|totale = totale * membro figlio corrente|  
|/|totale = totale / membro figlio corrente|  
|~|Il membro figlio non viene utilizzato nel rollup e il suo valore viene ignorato.|  
  
 È ad esempio possibile creare una proprietà di membro denominata **SALES_OPERATOR** alla quale possono essere assegnati gli operatori unari indicati nella tabella seguente.  
  
|Membro padre|Membro figlio|  
|-------------------|------------------|  
|Net Sales|Domestic Sales (+)<br /><br /> Domestic Returns (~)<br /><br /> Foreign Sales (+)<br /><br /> Foreign Returns (~)|  
  
 Con questa nuova proprietà di membro, l'istruzione MDX seguente esegue l'operazione di stima delle vendite lorde in modo rapido ed efficace, ignorando i resi nazionali ed esteri:  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 Quando la funzione viene chiamata, il valore di ogni membro figlio viene applicato a un totale utilizzando l'operatore archiviato nella proprietà del membro. I membri relativi ai resi nazionali ed esteri vengono ignorati e il totale di rollup restituito dalla funzione **RollupChildren** viene moltiplicato per 1,1.  
  
### <a name="using-the-iif-function"></a>Utilizzo della funzione IIf  
 Se invece l'operazione di esempio non deve essere eseguita di frequente o viene applicata solo a una query MDX, per ottenere lo stesso risultato è possibile usare la funzione [IIf](../../../mdx/iif-mdx.md) con la funzione **RollupChildren** . La query MDX seguente genera lo stesso risultato dell'esempio precedente, ma senza ricorrere a una proprietà di membro personalizzata:  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 L'istruzione MDX esamina l'operatore unario del membro figlio. Se l'operatore unario viene usato per eseguire una sottrazione, ad esempio quando sono presenti resi nazionali ed esteri, la funzione **IIf** sostituisce l'operatore unario ~, in caso contrario la funzione **IIf** usa l'operatore unario del membro figlio. Il totale di rollup restituito viene infine moltiplicato per 1,1 per determinare il valore della stima per le vendite nazionali ed estere lorde.  
  
## <a name="see-also"></a>Vedere anche  
 [Manipolazione dei dati &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  
