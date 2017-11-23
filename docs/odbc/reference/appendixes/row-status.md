---
title: Stato di riga | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60931ff8464478a55828713747ad6f4bb408f10d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="row-status"></a>Stato di riga
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori crea un buffer nella cache per lo stato di riga. La libreria di cursori recupera i valori per la matrice di stato di riga (specificato con l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR) da questo buffer. Per ogni riga, la libreria di cursori imposta questo buffer:  
  
-   SQL_ROW_DELETED durante l'esecuzione di un oggetto posizionato delete-istruzione nella riga.  
  
-   SQL_ROW_ERROR quando viene rilevato un errore nel recupero di righe dall'origine dati con **SQLFetch**.  
  
-   SQL_ROW_SUCCESS quando vengono recuperati correttamente la riga dall'origine dati con **SQLFetch**.  
  
-   SQL_ROW_UPDATED quando viene eseguita un'istruzione di aggiornamento posizionato sulla riga.
