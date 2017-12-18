---
title: YEAR (espressione SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea267c8f94fd2fb20c9c73bc29ec24820c0555a1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="year-ssis-expression"></a>YEAR (espressione SSIS)
  Viene restituito un valore integer che rappresenta la parte corrispondente all'anno di una data.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a>Argomenti  
 *data*  
 Data in qualsiasi formato di data.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Osservazioni  
 Se l'argomento è Null, YEAR restituirà Null.  
  
 Per i valori letterali di data è necessario eseguire il cast esplicito a uno dei tipi di dati date. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La convalida dell'espressione non riesce quando viene eseguito il cast esplicito di un valore letterale di data a uno di questi tipi di dati relativi alle date: DT_DBTIMESTAMPOFFSET e DT_DBTIMESTAMP2.  
  
 La funzione YEAR costituisce una forma più breve, ma equivalente, della funzione DATEPART("Year", date).  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito il numero dell'anno in un valore letterale di data. Se la data è in formato mm/gg/aaaa, l'esempio restituirà "2002".  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 In questo esempio viene restituito un Integer che rappresenta l'anno nella colonna **ModifiedDate** .  
  
```  
YEAR(ModifiedDate)  
```  
  
 In questo esempio viene restituito un valore integer che rappresenta l'anno nella data corrente.  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATEADD &#40;espressione SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;espressione SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;espressione SSIS&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;espressione SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;espressione SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
