---
title: "FLOOR (espressione SSIS) | Microsoft Docs"
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
  - "valore integer maggiore che risulta minore o uguale a un'espressione"
  - "FLOOR - funzione [SSIS]"
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# FLOOR (espressione SSIS)
  Restituisce il più alto valore integer minore o uguale a un'espressione numerica specificata.  
  
## Sintassi  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
## Tipi restituiti  
 Tipo di dati numeric dell'espressione passata come argomento. Il risultato è rappresentato dalla parte intera del valore calcolato con tipo di dati corrispondente al tipo del parametro *numeric_expression*.  
  
## Osservazioni  
 Se l'argomento è Null, FLOOR restituirà Null.  
  
## Esempi di espressione  
 In questi esempi la funzione FLOOR viene applicata a valori positivi, negativi e zero.  
  
```  
FLOOR(123.45)  
```  
  
 Restituisce 123,00.  
  
```  
FLOOR(-123.45)  
```  
  
 Restituisce -124,00.  
  
```  
FLOOR(0.00)  
```  
  
 Restituisce 0,00.  
  
## Vedere anche  
 [CEILING &#40;espressione SSIS&#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  