---
title: Istruzione DRILLTHROUGH (MDX) | Documenti Microsoft
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
- DRILLTHROUGH
dev_langs:
- kbMDX
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- data retrieval [MDX]
ms.assetid: dfa22755-0ed4-4bba-9c31-7ade26d9ebdb
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6beadd42ec1f41ccec1ce8b0df999897b50568f5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-manipulation---drillthrough"></a>Manipolazione dei dati MDX - drill-through
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Recupera le righe di tabella sottostanti utilizzate per creare una cella specificata in un cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Unsigned_Integer*  
 Valore integer positivo.  
  
 *Istruzione MDX SELECT*  
 Qualsiasi istruzione SELECT di espressione MDX (Multidimensional Expression) valida.  
  
 *Set_of_Attributes_and_Measures*  
 Elenco delimitato da virgole di misure e attributi della dimensione.  
  
## <a name="remarks"></a>Osservazioni  
 Il drill-through è un'operazione con cui un utente finale seleziona una singola cella di un cubo e recupera un set di risultati dai dati di origine di tale cella allo scopo di ottenere informazioni più dettagliate. Per impostazione predefinita, il set di risultati di un drill-through è derivato dalle righe di tabella che sono state valutate per calcolare il valore della cella del cubo selezionata. Per il drill-through da parte degli utenti finali, è necessario che le relative applicazioni client supportino tale funzionalità. In [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], i risultati vengono recuperati direttamente dall'archivio MOLAP, a meno che non vengono eseguite su partizioni o dimensioni ROLAP.  
  
> [!IMPORTANT]  
>  La sicurezza relativa al drill-through è basata sulle opzioni di sicurezza generali definite per il cubo. Se un utente non può ottenere alcuni dati tramite MDX, all'utente verranno applicate dal drill-through le stesse restrizioni.  
  
 La cella interessata è specificata da un'istruzione MDX. Il valore specificato per il **MAXROWS** argomento indica il numero massimo di righe che devono essere restituiti dal set di righe risultante.  
  
 Per impostazione predefinita, il numero massimo di righe restituite è 10.000. Ciò significa che se si lascia **MAXROWS** non viene specificato, si otterranno le righe di 10.000 o meno. Se questo valore è troppo basso per lo scenario, è possibile impostare **MAXROWS** su un numero più alto, ad esempio `MAXROWS 20000`. Se è troppo basso generale, è possibile aumentare il valore predefinito modificando il **OLAP\Query\DefaultDrillthroughMaxRows** proprietà del server. Per ulteriori informazioni sulla modifica di questa proprietà, vedere [Server Properties in Analysis Services](../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 Se non diversamente specificato, le colonne restituite includono tutti gli attributi di granularità per tutte le dimensioni correlate al gruppo di misure della misura specificata, tranne le dimensioni molti-a-molti. Le dimensioni del cubo sono precedute da $ per consentire la distinzione tra dimensioni e gruppi di misure. Il **restituire** clausola viene utilizzata per specificare le colonne restituite dalla query drill-through. Le funzioni seguenti possono essere applicate a un singolo attributo o misura mediante la **restituire** clausola.  
  
 Name(attribute_name)  
 Restituisce il nome del membro dell'attributo specificato.  
  
 UniqueName(attribute_name)  
 Restituisce il nome univoco del membro dell'attributo specificato.  
  
 Key(attribute_name[, N])  
 Restituisce la chiave del membro dell'attributo specificato. N specifica la colonna nella chiave composta (se disponibile). Il valore predefinito di N è 1.  
  
 Caption(attribute_name)  
 Restituisce la didascalia del membro dell'attributo specificato.  
  
 MemberValue(attribute_name)  
 Restituisce il valore del membro dell'attributo specificato.  
  
 CustomRollup(attribute_name)  
 Restituisce l'espressione di rollup personalizzato del membro dell'attributo specificato.  
  
 CustomRollupProperties(attribute_name)  
 Restituisce le proprietà di rollup personalizzato del membro dell'attributo specificato.  
  
 UnaryOperator(attribute_name)  
 Restituisce l'operatore unario del membro dell'attributo specificato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene specificata la cella del mese di luglio 2007 per la misura dell'importo delle vendite dei rivenditori (misura predefinita) per il paese Australia. La clausola RETURN specifica la restituzione della data di ogni vendita, del nome del modello di prodotto, del nome del dipendente, dell'importo delle vendite, delle imposte e dei valori di costo dei prodotti sottostanti questa cella.  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le istruzioni di manipolazione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
