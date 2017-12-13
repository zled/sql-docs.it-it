---
title: Creare query drill-through tramite DMX | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3b9487131e474dd00a25390a53cb5f3f11d07d2c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="create-drillthrough-queries-using-dmx"></a>Creare query drill-through tramite DMX
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Per tutti i modelli che supportano il drill-through, è possibile recuperare i dati del case e della struttura creando una query DMX in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o qualsiasi altro client che supporta DMX.  
  
> [!WARNING]  
>  Per visualizzare i dati, è necessario aver abilitato il drill-through e disporre delle autorizzazioni necessarie.  
  
## <a name="specifying-drillthrough-options"></a>Impostazione delle opzioni di drill-through  
 La sintassi generale per il recupero di case del modello e di case della struttura è la seguente:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 Per altre informazioni sull'utilizzo di query DMX per restituire dati del case, vedere [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](../../dmx/select-from-model-cases-dmx.md) e [SELECT FROM &#60;structure&#62;.CASES](../../dmx/select-from-structure-cases.md).  
  
## <a name="examples"></a>Esempi  
 La query DMX seguente restituisce i dati del case relativi a una serie di prodotti specifica da un modello Time Series. La query restituisce anche la colonna **Amount**che non viene utilizzata nel modello, ma risulta disponibile nella struttura di data mining.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 In questo esempio viene utilizzato un alias per rinominare la colonna della struttura. Se non si assegna un alias alla colonna della struttura, la colonna viene restituita con il nome 'Expression'. Si tratta del comportamento predefinito per tutte le colonne senza nome.  
  
## <a name="see-also"></a>Vedere anche  
 [Query drill-through &#40;Data mining&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Drill-through sulle strutture di data mining](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  
