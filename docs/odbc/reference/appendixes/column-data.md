---
title: Dati della colonna | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1aa5125d58c2d630a9233b5564ad3c58203a669f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="column-data"></a>Dati della colonna
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori consente di creare un buffer nella cache per ogni buffer di dati associato al set di risultati con **SQLBindCol**. Utilizza i valori in questi buffer per costruire un **dove** clausola quando emula un posizionato istruzioni update o delete. Aggiorna i buffer dai buffer di set di righe durante il recupero dei dati dall'origine dei dati e quando esegue le istruzioni per gli aggiornamenti posizionati.  
  
 Quando la libreria di cursori Aggiorna la cache dai buffer di set di righe, di trasferire i dati in base al tipo di dati C specificato in **SQLBindCol**. Ad esempio, se il tipo di dati C di un buffer di set di righe è SQL_C_SLONG, la libreria di cursori trasferito quattro byte di dati. Se è SQL_C_CHAR e *BufferLength* è 10, la libreria di cursori trasferisce 10 byte di dati. La libreria di cursori non esegue alcun controllo dei tipi o conversioni sui dati che vengono trasferiti.  
  
> [!NOTE]  
>  La libreria di cursori non aggiorna la cache per una colonna se **StrLen_or_IndPtr* nel set di righe corrispondente buffer è SQL_DATA_AT_EXEC o il risultato della macro SQL_LEN_DATA_AT_EXEC.  
  
 Quando aggiorna una colonna, dei dati dell'origine vuoto riempie caratteri a lunghezza fissa e dati binari a lunghezza fissa fino a zero in base alle esigenze. Ad esempio, un'origine dati memorizza "Smith" in una colonna char (10) come "Smith". La libreria di cursori non non vuoto-riquadro o zero-riquadro dati nei buffer di set di righe durante la copia di dati nella cache dopo l'esecuzione di un'istruzione di aggiornamento posizionato. Pertanto, se un'applicazione richiede che i valori nella cache della libreria di cursori sono riempiti con spazio vuoto o riempiti con degli zero, deve vuoto-riquadro o zero-riquadro i valori nei buffer di set di righe prima di eseguire un'istruzione di aggiornamento posizionato.
