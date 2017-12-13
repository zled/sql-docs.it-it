---
title: Colonne del modello di data mining | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0acbc12c9aa0d553bfee5e9e11dcb098547288c7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="mining-model-columns"></a>Colonne del modello di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Un modello di data mining applica un algoritmo del modello di data mining ai dati che sono rappresentati da una struttura di data mining. Analogamente alla struttura, il modello di data mining contiene colonne. Un modello di data mining è contenuto all'interno della struttura di data mining ed eredita tutti i valori delle proprietà definite dalla struttura. Nel modello possono essere utilizzate tutte le colonne contenute nella struttura di data mining o un subset delle colonne.  
  
 In una colonna di un modello di data mining è possibile definire due informazioni aggiuntive, cioè utilizzo e flag di modellazione.  
  
-   **Usage** è una proprietà che definisce il modo in cui il modello usa la colonna. Le colonne possono essere utilizzate come colonne di input, colonne chiave o colonne stimabili.  
  
-   I**flag di modellazione** offrono all'algoritmo altre informazioni sui dati definiti nella tabella del case per consentire la compilazione di un modello più preciso. È possibile definire flag di modellazione a livello di programmazione usando il linguaggio DMX (Data Mining Extensions) o tramite **Progettazione modelli di data mining** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Nell'elenco seguente vengono descritti i flag di modellazione che è possibile definire in una colonna di un modello di data mining.  
  
 **MODEL_EXISTENCE_ONLY**  
 Indica che la presenza dell'attributo è più importante rispetto ai valori nella colonna attributo. Si consideri, ad esempio, una tabella del case contenente un elenco di elementi ordinati associati a un cliente specifico. I dati della tabella includono tipo di prodotto, ID e costo di ogni elemento. Ai fini della modellazione, il fatto che il cliente abbia acquistato un determinato articolo potrebbe essere più importante rispetto al costo dell'articolo stesso. In questo caso, la colonna del costo deve essere contrassegnata come **MODEL_EXISTENCE_ONLY**.  
  
 **REGRESSOR**  
 Indica che l'algoritmo può utilizzare la colonna specificata nella formula di regressione degli algoritmi di regressione. Questo flag è supportato dagli algoritmi [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series.  
  
 Per altre informazioni sull'impostazione della proprietà di utilizzo e sulla definizione di flag di modellazione a livello di programmazione tramite DMX, vedere [CREATE MINING MODEL &#40;DMX&#41;](../../dmx/create-mining-model-dmx.md). Per altre informazioni sull'impostazione della proprietà di utilizzo e sulla definizione di flag di modellazione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vedere [Spostamento di oggetti di data mining](../../analysis-services/data-mining/moving-data-mining-objects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Strutture di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modificare le proprietà di un modello di Data Mining](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)   
 [Escludere una colonna da un modello di Data Mining](../../analysis-services/data-mining/exclude-a-column-from-a-mining-model.md)   
 [Colonne della struttura di data mining](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
