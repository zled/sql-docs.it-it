---
title: Stato di riga | Documenti Microsoft
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba4f36ad63ee5e7d9fada29d444e8cc36eca1bcf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906306"
---
# <a name="row-status"></a>Stato di riga
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori crea un buffer nella cache per lo stato di riga. La libreria di cursori recupera i valori per la matrice di stato di riga (specificato con l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR) da questo buffer. Per ogni riga, la libreria di cursori imposta questo buffer:  
  
-   SQL_ROW_DELETED durante l'esecuzione di un oggetto posizionato delete-istruzione nella riga.  
  
-   SQL_ROW_ERROR quando viene rilevato un errore nel recupero di righe dall'origine dati con **SQLFetch**.  
  
-   SQL_ROW_SUCCESS quando vengono recuperati correttamente la riga dall'origine dati con **SQLFetch**.  
  
-   SQL_ROW_UPDATED quando viene eseguita un'istruzione di aggiornamento posizionato sulla riga.
