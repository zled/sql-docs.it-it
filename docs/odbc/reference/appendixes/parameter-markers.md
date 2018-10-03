---
title: Marcatori di parametro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ac59cddb24d5e08e3b620c178f40e206460eb7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835419"
---
# <a name="parameter-markers"></a>Marcatori di parametro
Conforme alla specifica di SQL-92, un'applicazione non è possibile posizionare gli indicatori di parametro nelle posizioni seguenti. Per un elenco più completo, vedere la specifica di SQL-92.  
  
-   In un **seleziona** elenco  
  
-   Come entrambe *expressions* in un *predicato di confronto*  
  
-   Come entrambi gli operandi dell'operatore binario  
  
-   Come entrambi gli operandi primi e la secondo di una **BETWEEN** operazione  
  
-   Come operandi del primo e del terzo di una **BETWEEN** operazione  
  
-   Come l'espressione sia il primo valore di un' **India** operazione  
  
-   Come operando di unario + o -operazione  
  
-   Come argomento di un *set-funzione-reference*  
  
 Per altre informazioni sui marcatori di parametro, vedere la specifica di SQL-92. Per altre informazioni sui parametri, vedere [parametri delle istruzioni](../../../odbc/reference/develop-app/statement-parameters.md).
