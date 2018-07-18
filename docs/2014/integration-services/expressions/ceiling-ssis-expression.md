---
title: CEILING (espressione SSIS) | Microsoft Docs
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
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6b7b6afd3879805c0badc1c15e6113971dcb776a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065626"
---
# <a name="ceiling-ssis-expression"></a>CEILING (espressione SSIS)
  Restituisce il più piccolo valore integer maggiore o uguale a un'espressione numerica specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
## <a name="result-types"></a>Tipi restituiti  
 Tipo di dati dell'espressione numerica inviata alla funzione.  
  
## <a name="remarks"></a>Remarks  
 Se l'argomento è Null, CEILING restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi la funzione CEILING viene applicata a valori positivi, negativi e zero.  
  
```  
CEILING(123.74)  
```  
  
 Restituisce 124,00.  
  
```  
CEILING(-124.27)  
```  
  
 Restituisce -124,00.  
  
```  
CEILING(0.00)  
```  
  
 Restituisce 0,00.  
  
## <a name="see-also"></a>Vedere anche  
 [PIANO &#40;espressione SSIS&#41;](floor-ssis-expression.md)   
 [Le funzioni &#40;espressione SSIS&#41;](functions-ssis-expression.md)  
  
  