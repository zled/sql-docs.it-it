---
title: Stato di riga | Documenti Microsoft
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f164b8269e1150cdf7a85e486bcc3fd93a9411f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="row-status"></a>Stato di riga
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori crea un buffer nella cache per lo stato di riga. La libreria di cursori recupera i valori per la matrice di stato di riga (specificato con l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR) da questo buffer. Per ogni riga, la libreria di cursori imposta questo buffer:  
  
-   SQL_ROW_DELETED durante l'esecuzione di un oggetto posizionato delete-istruzione nella riga.  
  
-   SQL_ROW_ERROR quando viene rilevato un errore nel recupero di righe dall'origine dati con **SQLFetch**.  
  
-   SQL_ROW_SUCCESS quando vengono recuperati correttamente la riga dall'origine dati con **SQLFetch**.  
  
-   SQL_ROW_UPDATED quando viene eseguita un'istruzione di aggiornamento posizionato sulla riga.
