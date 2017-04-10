---
title: "ABS (espressione SSIS) | Microsoft Docs"
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
  - "ABS - funzione"
  - "valore assoluto positivo"
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ABS (espressione SSIS)
  Restituisce il valore positivo assoluto di un'espressione numerica.  
  
## Sintassi  
  
```  
  
ABS(numeric_expression)  
```  
  
## Argomenti  
 *numeric_expression*  
 Espressione numerica con o senza segno.  
  
## Tipi restituiti  
 Tipo di dati dell'espressione numerica inviata alla funzione.  
  
## Osservazioni  
 Se l'argomento è Null, ABS restituirà Null.  
  
## Esempi di espressione  
 In questi esempi la funzione ABS viene applicata a un numero positivo e a un numero negativo. In entrambi i casi viene restituito 1,23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 In questo esempio la funzione ABS viene applicata a un'espressione che esegue una sottrazione tra i valori delle variabili **HighTemperature** e **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  