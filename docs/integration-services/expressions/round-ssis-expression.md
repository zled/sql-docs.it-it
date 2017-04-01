---
title: "ROUND (espressione SSIS) | Microsoft Docs"
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
  - "arrotondamento di espressioni"
  - "ROUND - funzione [SSIS]"
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# ROUND (espressione SSIS)
  Restituisce un'espressione numerica arrotondata alla lunghezza o alla precisione specificata. Il parametro length deve restituire un valore integer.  
  
## Sintassi  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## Argomenti  
 *numeric_expression*  
 Espressione di tipo numeric valido. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *lunghezza*  
 Espressione integer. Precisione per l'arrotondamento di *numeric_expression*.  
  
## Tipi restituiti  
 Tipo identico a *numeric*_*expression*.  
  
## Osservazioni  
 Tramite l'argomento *length* deve essere restituito un numero intero positivo oppure zero.  
  
 Se l'argomento è Null, ROUND restituirà Null.  
  
## Esempi di espressione  
 In questi esempi alcuni valori letterali numerici vengono arrotondati con lunghezza tre. Il primo risultato restituito è 137,1570, il secondo 137,1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  