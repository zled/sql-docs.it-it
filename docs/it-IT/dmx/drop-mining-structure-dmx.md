---
title: ELIMINARE LA STRUTTURA DI DATA MINING (DMX) | Documenti Microsoft
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
f1_keywords:
- DROP MINING STRUCTURE
- DROP_MINING_STRUCTURE
dev_langs:
- DMX
helpviewer_keywords:
- removing mining structures
- dropping mining structures
- DROP MINING STRUCTURE statement
- deleting mining structures
- mining structures [DMX], deleting
ms.assetid: 30df8c36-3a15-4d8c-98f3-0f8917be9fc8
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ce04f32c33974a98baaded34fcd3d6e09f9c9373
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Elimina dal database la struttura di data mining specificata. Dal database verranno eliminati anche tutti i modelli di data mining associati alla struttura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP MINING STRUCTURE <structure>  
```  
  
## <a name="arguments"></a>Argomenti  
 *struttura*  
 Identificatore della struttura.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminata la struttura di data mining New Mailing dal database.  
  
```  
DROP MINING STRUCTURE [New Mailing]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
