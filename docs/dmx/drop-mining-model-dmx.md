---
title: ELIMINARE IL MODELLO DI DATA MINING (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
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
ms.topic: language-reference
f1_keywords: DROP_MINING_MODEL
dev_langs: DMX
helpviewer_keywords:
- DROP MINING MODEL statement
- deleting mining models
- removing mining models
- dropping mining models
- mining models [Analysis Services], deleting
ms.assetid: 8ff561d0-a526-4712-9fff-11df9f8c45a1
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6f3615d4361ed8e976524dd717fc9bd8399b1888
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="drop-mining-model-dmx"></a>DROP MINING MODEL (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Elimina un modello di data mining dal database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP MINING MODEL <model >  
```  
  
## <a name="arguments"></a>Argomenti  
 *model*  
 Identificatore del modello.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio di codice seguente viene eliminato il modello di data mining NBSample.  
  
```  
DROP MINING MODEL [NBSample]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
