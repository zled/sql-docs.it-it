---
title: "REVERSE (espressione SSIS) | Microsoft Docs"
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
  - "REVERSE - funzione"
  - "inversione di espressioni di caratteri"
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# REVERSE (espressione SSIS)
  Viene restituita un'espressione di caratteri in ordine inverso.  
  
## Sintassi  
  
```  
  
REVERSE(character_expression)  
```  
  
## Argomenti  
 *character_expression*  
 Espressione di caratteri da invertire.  
  
## Tipi restituiti  
 DT_WSTR  
  
## Osservazioni  
 Il tipo di dati dell’argomento *character_expression* deve essere DT_WSTR.  
  
 Se *character_expression* è null, REVERSE restituisce un risultato null.  
  
## Esempi di espressione  
 In questo esempio viene utilizzato un valore letterale stringa. Il risultato restituito è "ekiB niatnuoM".  
  
```  
REVERSE("Mountain Bike")  
```  
  
 In questo esempio viene utilizzata una variabile. Se **Name** contiene Touring Bike, il risultato restituito sarà "ekiB gniruoT".  
  
```  
REVERSE(@Name)  
```  
  
## Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  