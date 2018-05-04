---
title: Il recupero dei segnalibri | Documenti Microsoft
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
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a78b232a1cdb5564388cdf9b335a5ce06cfcb68
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-bookmarks"></a>Il recupero dei segnalibri
Se l'applicazione utilizzerà i segnalibri, è necessario impostare l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS per SQL_UB_VARIABLE prima di preparazione o l'esecuzione dell'istruzione. Ciò è necessario perché la creazione e la gestione di segnalibri possono essere un'operazione dispendiosa, pertanto i segnalibri devono essere abilitati solo quando un'applicazione può effettuare buona loro utilizzo.  
  
 I segnalibri vengono restituiti come colonna 0 del set di risultati. Sono disponibili in un'applicazione è possibile recuperarle in tre modi:  
  
-   Associare la colonna 0 del set di risultati. **SQLFetch** oppure **SQLFetchScroll** restituisce i segnalibri per ogni riga nel set di righe insieme ai dati per altri colonne associate.  
  
-   Chiamare **SQLSetPos** per posizionarsi su una riga nel set di righe e quindi chiamare **SQLGetData** per la colonna 0. Se un driver supporta i segnalibri, deve supportare sempre la possibilità di chiamare **SQLGetData** per la colonna 0, anche se non consente alle applicazioni di chiamare **SQLGetData** per le altre colonne prima il limite ultimo colonna.  
  
-   Chiamare **SQLBulkOperations** con il *operazione* argomento impostato su SQL_ADD e colonna 0 associato. Il cursore inserisce la riga e restituisce il segnalibro per la riga nel buffer associato.
