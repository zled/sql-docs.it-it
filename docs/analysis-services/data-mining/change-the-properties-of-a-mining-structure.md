---
title: Modificare le proprietà di una struttura di Data Mining | Documenti Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2f97c94a1c594a341c1e03326c975a080d9033cf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="change-the-properties-of-a-mining-structure"></a>Modificare le proprietà di una struttura di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Esistono due tipi di proprietà su una struttura di data mining, che può essere modificati:  
  
-   Proprietà della struttura di data mining che influiscono sull'intera struttura  
  
-   Proprietà su singole colonne della struttura  
  
 Si noti che alcune proprietà dipendono da altre impostazioni di proprietà. Non è ad esempio possibile impostare le proprietà che controllano la creazione di contenitori, ad esempio <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> o <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>finché non viene impostato il tipo di dati della colonna su **Discretized**.  
  
 Per altre informazioni sulle proprietà di data mining, vedere [Colonne della struttura di data mining](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>Per modificare le proprietà di una struttura di data mining  
  
1.  Nella scheda **Struttura di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla struttura di data mining o su una colonna della struttura e quindi scegliere **Proprietà**.  
  
     A destra dello schermo verrà visualizzata la finestra **Proprietà** , se non è già visualizzata.  
  
2.  Nella finestra **Proprietà** selezionare il valore corrispondente alla proprietà che si vuole modificare e quindi immettere il nuovo valore.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
