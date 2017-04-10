---
title: "LTRIM (espressione SSIS) | Microsoft Docs"
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
  - "spazi vuoti iniziali"
  - "LTRIM - funzione"
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LTRIM (espressione SSIS)
  Restituisce un'espressione di caratteri dopo aver rimosso gli spazi iniziali.  
  
> [!NOTE]  
>  LTRIM non rimuove altri caratteri spazio, quali i caratteri di tabulazione o avanzamento riga. Unicode offre elementi di codice per molti tipi diversi di spazi, ma questa funzione riconosce solo l'elemento di codice Unicode 0x0020. Quando stringhe DBCS (Double-Byte Character Set) vengono convertite in Unicode, possono includere caratteri spazio diversi da 0x0020 e la funzione non può rimuovere tali spazi. Per rimuovere qualsiasi tipo di spazi, è possibile utilizzare il metodo Microsoft Visual Basic .NET LTrim in uno script eseguito dal componente Script.  
  
## Sintassi  
  
```  
  
LTRIM(character expression)  
```  
  
## Argomenti  
 *character_expression*  
 Espressione di caratteri da cui rimuovere gli spazi.  
  
## Tipi restituiti  
 DT_WSTR  
  
## Osservazioni  
 È possibile utilizzare LTRIM solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da LTRIM verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, LTRIM restituirà Null.  
  
## Esempi di espressione  
 In questo esempio vengono rimossi gli spazi iniziali da un valore letterale stringa. Il risultato restituito è "Hello".  
  
```  
LTRIM("    Hello")  
```  
  
 In questo esempio vengono rimossi gli spazi iniziali dalla colonna **FirstName** .  
  
```  
LTRIM(FirstName)  
```  
  
 In questo esempio vengono rimossi gli spazi iniziali dalla variabile **FirstName** .  
  
```  
LTRIM(@FirstName)  
```  
  
## Vedere anche  
 [RTRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [TRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  