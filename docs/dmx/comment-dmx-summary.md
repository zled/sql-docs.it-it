---
title: -(Commento) (DMX) riepilogo | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- commenting characters
- double hyphens
- -- (comment character)
ms.assetid: 487b580b-5b81-4e52-8868-4fa809e4ef58
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0ab3cef118685094ae96e02dcbf6b994e1157cd0
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="---comment-dmx-summary"></a>-(Commento) (DMX) riepilogo
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indica una stringa di testo che non deve essere eseguita da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. I commenti possono essere nidificati in un'espressione DMX (Data Mining Extensions), inclusi alla fine di una riga di codice o inseriti su una riga distinta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Parametri  
 *Comment_Text*  
 Stringa contenente il testo del commento.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare questo operatore per commenti su una sola riga o nidificati. I commenti inseriti tramite -- sono delimitati dal carattere di nuova riga.  
  
 I commenti possono essere di qualsiasi lunghezza.  
  
 Per ulteriori informazioni sull'utilizzo di diversi tipi di commenti in DMX, vedere [DMX commenti &#40; &#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stella barra &#40; Commento &#41; &#40; DMX &#41;](../dmx/slash-star-comment-dmx.md)   
 [Doppia barra &#40; Commento &#41; &#40; DMX &#41;](../dmx/double-slash-comment-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  

