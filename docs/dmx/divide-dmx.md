---
title: (Divisione) (DMX) | Documenti Microsoft
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
- / (divide)
- divide operator (/)
ms.assetid: 7afc06cd-054b-48c3-9c3c-9a0c17d15e63
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8485c6e5cb68fcfd07f1ee812ba4c9a7035b1931
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="divide-dmx"></a>(Divisione) (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue un'operazione aritmetica di divisione di un numero per un altro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Parametri  
 *Dividendo*  
 Espressione DMX (Data Mining Extensions) valida che restituisce un valore numerico.  
  
 *Divisore*  
 Espressione DMX valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore con il tipo di dati del parametro con precedenza maggiore.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore restituito da questo operatore rappresenta il quoziente della divisione tra la prima e la seconda espressione.  
  
 È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione. Se il divisore restituisce un valore Null, verrà generato un errore. Se il divisore e il dividendo restituiscono entrambi un valore Null, l'operatore restituirà un valore Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Aritmetici operatori &#40; DMX &#41;](../dmx/operators-arithmetic.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)   
 [Divisione &#40; Espressione SSIS &#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40; divisione &#41; &#40; Transact-SQL &#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  

