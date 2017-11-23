---
title: Barre a stella (commento) (DMX) | Documenti Microsoft
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
dev_langs: DMX
helpviewer_keywords:
- commenting characters
- forward slash-asterisk character pairs
- /*...*/ (comment)
ms.assetid: 163976cc-aa47-4eda-bd98-03c1a397f80e
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 0d458e95075bb96154d14a935d5aa5cba839d752
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="slash-star-comment-dmx"></a>Barre a stella (commento) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica una stringa di testo che non deve essere eseguita da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Il server non valuta il testo tra i caratteri di commento / * e \*/. I commenti possono essere nidificati in un'espressione DMX (Data Mining Extensions), inclusi alla fine di una riga di codice o inseriti su una riga distinta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>Parametri  
 *Comment_Text*  
 Stringa contenente il testo del commento.  
  
## <a name="remarks"></a>Osservazioni  
 Commenti su più righe devono essere contrassegnati da / * e \*/.  
  
 I commenti possono essere di qualsiasi lunghezza.  
  
 Per ulteriori informazioni sull'utilizzo di diversi tipi di commenti in DMX, vedere [DMX commenti &#40; &#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Doppia barra &#40; Commento &#41; &#40; DMX &#41;](../dmx/double-slash-comment-dmx.md)   
 [-&#40; Commento &#41; &#40; DMX &#41; Riepilogo](../dmx/comment-dmx-summary.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  
