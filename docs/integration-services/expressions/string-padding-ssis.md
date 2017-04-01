---
title: "Riempimento di stringhe (SSIS) | Microsoft Docs"
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
  - "riempimento di stringhe [Integration Services]"
  - "espressioni [Integration Services], riempimento di stringhe"
  - "riempimento di stringhe"
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Riempimento di stringhe (SSIS)
  L'analizzatore di espressioni non verifica se una stringa contiene spazi iniziali e finali, né applica riempimenti alle stringhe in modo che abbiano la stessa lunghezza, prima di confrontarle. Nelle espressioni che richiedono il riempimento delle stringhe è possibile utilizzare l'operatore + per concatenare valori di colonna e stringhe vuote. Per altre informazioni, vedere [+ &#40;concatenazione&#41; &#40;espressione SSIS&#41;](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 Se invece è necessario rimuovere spazi, l'analizzatore di espressioni fornisce le funzioni LTRIM, RTRIM e TRIM, che consentono di rimuovere gli spazi iniziali, gli spazi finali o entrambi. Per altre informazioni, vedere [LTRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md) e [TRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  La funzione LEN include nel conteggio anche gli spazi vuoti iniziali e finali.  
  
## Contenuto correlato  
 Articolo tecnico relativo al [foglio d'aiuto per le espressioni SSIS](http://go.microsoft.com/fwlink/?LinkId=746575)sul sito Web pragmaticworks.com  
  
  