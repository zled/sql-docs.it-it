---
title: "CEILING (espressione SSIS) | Microsoft Docs"
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
  - "più piccolo valore intero maggiore o uguale a un'espressione"
  - "CEILING - funzione [SSIS]"
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# CEILING (espressione SSIS)
  Restituisce il più piccolo valore integer maggiore o uguale a un'espressione numerica specificata.  
  
## Sintassi  
  
```  
  
CEILING(numeric_expression)  
```  
  
## Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
## Tipi restituiti  
 Tipo di dati dell'espressione numerica inviata alla funzione.  
  
## Osservazioni  
 Se l'argomento è Null, CEILING restituirà Null.  
  
## Esempi di espressione  
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
  
## Vedere anche  
 [FLOOR &#40;espressione SSIS&#41;](../../integration-services/expressions/floor-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  