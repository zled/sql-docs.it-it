---
title: CODEPOINT (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 916077a69ca54616cf8e0bb7e8d0144aeba186df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686159"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (espressione SSIS)
  Viene restituito l'elemento di codice Unicode del carattere più a sinistra di un'espressione di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri di cui restituire il primo carattere a sinistra.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_UI2  
  
## <a name="remarks"></a>Remarks  
 Il tipo di dati di*character_expression* deve essere DT_WSTR.  
  
 Se il parametro *character_expression* è una stringa vuota o Null, tramite CODEPOINT verrà restituito Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene utilizzato un valore letterale stringa. Il risultato restituito è 77, l'elemento di codice Unicode corrispondente alla lettera M.  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 In questo esempio viene utilizzata una variabile. Se **Name** contiene la stringa Touring Front Wheel, il risultato restituito sarà 84, l'elemento di codice Unicode corrispondente alla lettera T.  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
