---
title: GIORNO (espressione SSIS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5e297f7021239ded4aa76ad61e75fddba528ccf6
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="day-ssis-expression"></a>DAY (espressione SSIS)
  Viene restituito un valore integer che rappresenta la parte del giorno in una data.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>Argomenti  
 *data*  
 Espressione che restituisce una data valida o una stringa con formato di data.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Osservazioni  
 Se l'argomento è Null, DAY restituirà Null.  
  
 Per i valori letterali di data è necessario eseguire il cast esplicito a uno dei tipi di dati date. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La convalida dell'espressione non riesce quando viene eseguito il cast esplicito di un valore letterale di data a uno di questi tipi di dati relativi alle date: DT_DBTIMESTAMPOFFSET e DT_DBTIMESTAMP2.  
  
 La funzione DAY costituisce una forma più breve, ma equivalente, della funzione DATEPART("Day", date).  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito il numero del giorno in un valore letterale di data. Se la data è in formato "mm/gg/aaaa", l'esempio restituirà 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 In questo esempio viene restituito un Integer che rappresenta il giorno nella colonna **ModifiedDate** .  
  
```  
DAY(ModifiedDate)  
```  
  
 In questo esempio viene restituito un valore integer che rappresenta il giorno nella data corrente.  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATEADD &#40; Espressione SSIS &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40; Espressione SSIS &#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40; Espressione SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [MESE &#40; Espressione SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [ANNO &#40; Espressione SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

