---
title: SIGN (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a68d4a3879c173298b99c305702aaaf61d43a194
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069878"
---
# <a name="sign-ssis-expression"></a>SIGN (espressione SSIS)
  Viene restituito il segno positivo (+1), negativo (-1) o zero (0) di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida con segno. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Se l'argomento è Null, SIGN restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito il segno di un valore letterale numerico. Il risultato restituito sarà -1.  
  
```  
SIGN(-123.45)  
```  
  
 In questo esempio viene restituito il segno del risultato della sottrazione della colonna **StandardCost** dalla colonna **DealerPrice** .  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni &#40;espressione SSIS&#41;](functions-ssis-expression.md)  
  
  