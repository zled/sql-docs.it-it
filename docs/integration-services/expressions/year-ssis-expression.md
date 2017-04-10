---
title: "YEAR (espressione SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "date [Integration Services], YEAR"
  - "YEAR - funzione"
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# YEAR (espressione SSIS)
  Viene restituito un valore integer che rappresenta la parte corrispondente all'anno di una data.  
  
## Sintassi  
  
```  
  
YEAR(date)  
```  
  
## Argomenti  
 *data*  
 Data in qualsiasi formato di data.  
  
## Tipi restituiti  
 DT_I4  
  
## Osservazioni  
 Se l'argomento è Null, YEAR restituirà Null.  
  
 Per i valori letterali di data è necessario eseguire il cast esplicito a uno dei tipi di dati date. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La convalida dell'espressione non riesce quando viene eseguito il cast esplicito di un valore letterale di data a uno di questi tipi di dati relativi alle date: DT_DBTIMESTAMPOFFSET e DT_DBTIMESTAMP2.  
  
 La funzione YEAR costituisce una forma più breve, ma equivalente, della funzione DATEPART("Year", date).  
  
## Esempi di espressione  
 In questo esempio viene restituito il numero dell'anno in un valore letterale di data. Se la data è in formato mm/gg/aaaa, l'esempio restituirà "2002".  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 In questo esempio viene restituito un Integer che rappresenta l'anno nella colonna **ModifiedDate**.  
  
```  
YEAR(ModifiedDate)  
```  
  
 In questo esempio viene restituito un valore integer che rappresenta l'anno nella data corrente.  
  
```  
YEAR(GETDATE())  
```  
  
## Vedere anche  
 [DATEADD &#40;espressione SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;espressione SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;espressione SSIS&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;espressione SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;espressione SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  