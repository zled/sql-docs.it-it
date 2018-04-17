---
title: Percorso della Cache | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5798f94d1ac4d3c5f3132a955cd465e22ff0e19
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="location-of-cache"></a>Percorso della Cache
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori memorizza i dati in memoria e nei file temporanei Windows®. Ciò limita le dimensioni del set di risultati che è in grado di gestire la libreria di cursori solo dallo spazio su disco disponibile. Un file temporaneo viene utilizzato quando i dati da memorizzare nella cache sarebbero superano il limite del segmento se inserito alla fine della cache di libreria del cursore. Al contrario, i dati da memorizzare nella cache vengono aggiunti al posto del blocco ultimo salvataggio dei dati nella cache. Il blocco ultimo salvataggio dei dati viene salvato in un file temporaneo. Se la libreria di cursori termina in modo anomalo, ad esempio quando la potenza ha esito negativo, è possibile lasciare i file temporanei di Windows sul disco. Queste sono denominate ~ CTT*nnnn*TMP e vengono creati nella directory corrente.  
  
> [!NOTE]  
>  Se la libreria di cursori in Microsoft® WindowsNT®/Windows 2000 tenta di memorizzare i dati in un file temporaneo nella directory corrente, mentre l'applicazione è in esecuzione da una condivisione di sola lettura o di un CD (ad esempio, un esempio di libreria Microsoft Foundation Class), SQLSTATE HY000 verrà restituito (generale errore-Unable per creare un buffer di file).
