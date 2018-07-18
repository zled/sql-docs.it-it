---
title: Marcatori di parametro | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df895c9e9956c1fde178824d1e14030246710946
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-markers"></a>Marcatori di parametro
Conforme alla specifica di SQL-92, un'applicazione non è possibile posizionare gli indicatori di parametro nei percorsi seguenti. Per un elenco più completo, vedere la specifica di SQL-92.  
  
-   In un **selezionare** elenco  
  
-   Sia come *espressioni* in un *predicato di confronto*  
  
-   In entrambi gli operandi dell'operatore binario  
  
-   Come entrambi gli operandi primo e secondo di un **BETWEEN** operazione  
  
-   Come il primo e il terzo operandi di un **BETWEEN** operazione  
  
-   L'espressione sia il primo valore di come un **IN** operazione  
  
-   Come operando di unario + o -operazione  
  
-   Come argomento di un *riferimento alle funzioni set*  
  
 Per ulteriori informazioni su marcatori di parametro, vedere la specifica di SQL-92. Per ulteriori informazioni sui parametri, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md).
