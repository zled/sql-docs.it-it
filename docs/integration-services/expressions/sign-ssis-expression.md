---
title: "SIGN (espressione SSIS) | Microsoft Docs"
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
  - "valori positivi [Integration Services]"
  - "SIGN - funzione"
  - "valori negativi"
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# SIGN (espressione SSIS)
  Viene restituito il segno positivo (+1), negativo (-1) o zero (0) di un'espressione numerica.  
  
## Sintassi  
  
```  
  
SIGN(numeric_expression)  
```  
  
## Argomenti  
 *numeric_expression*  
 Espressione numerica valida con segno. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Tipi restituiti  
 DT_I4  
  
## Osservazioni  
 Se l'argomento è Null, SIGN restituirà Null.  
  
## Esempi di espressione  
 In questo esempio viene restituito il segno di un valore letterale numerico. Il risultato restituito sarà -1.  
  
```  
SIGN(-123.45)  
```  
  
 In questo esempio viene restituito il segno del risultato della sottrazione della colonna **StandardCost** dalla colonna **DealerPrice**.  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  