---
title: Marcatori di parametro | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c2c8708c18abee3609fc0b01f6ccd2e0362e5706
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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

