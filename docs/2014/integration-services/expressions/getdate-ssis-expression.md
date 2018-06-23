---
title: GETDATE (espressione SSIS) | Microsoft Docs
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
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9161d114b9f103dc857c26a07b3c107d14a00b40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168340"
---
# <a name="getdate-ssis-expression"></a>GETDATE (espressione SSIS)
  Viene restituita la data corrente del sistema in formato DT_DBTIMESTAMP. La funzione GETDATE non accetta argomenti.  
  
> [!NOTE]  
>  La lunghezza del risultato restituito dalla funzione GETDATE è 29 caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Argomenti  
 None  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito l'anno della data corrente.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 Questo esempio restituisce il numero di giorni tra una data nella colonna **ModifiedDate** e la data corrente.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 In questo esempio vengono aggiunti tre mesi alla data corrente.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GETUTCDATE &#40;espressione SSIS&#41;](getutcdate-ssis-expression.md)   
 [Le funzioni &#40;espressione SSIS&#41;](functions-ssis-expression.md)  
  
  