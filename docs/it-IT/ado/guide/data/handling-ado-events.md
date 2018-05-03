---
title: Gestione degli eventi ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
- event handlers [ADO]
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b84df66d25c4e1ccda2330ccb1b0d02ff89dc20c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="handling-ado-events"></a>Gestione degli eventi ADO
Il modello di eventi ADO supporta determinate operazioni ADO sincrone e asincrone che rilasciano *eventi*, o notifiche, prima dell'inizio dell'operazione o quando è stata completata. Un evento è effettivamente una chiamata a una routine del gestore eventi definiti nell'applicazione.  
  
 Se si fornisce funzioni di gestione o le procedure per il gruppo di eventi che si verificano prima dell'inizio dell'operazione, è possibile esaminare o modificare i parametri passati all'operazione. Poiché non è stata eseguita ancora, è possibile annullare l'operazione o consentire il completamento.  
  
 Gli eventi che si verificano dopo il completamento di un'operazione sono particolarmente importanti se si utilizza ADO in modo asincrono. Ad esempio, un'applicazione che avvia un'operazione [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) operazione riceve una notifica tramite un evento di completamento dell'esecuzione alla conclusione dell'operazione.  
  
 Utilizzo del modello di evento ADO aggiunge overhead per l'applicazione ma molto più flessibile rispetto ad altri metodi di gestione delle operazioni asincrone, ad esempio monitoraggio di [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà di un oggetto con un ciclo.  
  
> [!NOTE]
>  Per gestire gli eventi, ADO deve disporre di un message pump oppure essere utilizzata in un modello di apartment a thread singolo (STA). Gli eventi ADO vengono gestiti internamente tramite la creazione di una finestra nascosta. ADO invia messaggi a questa finestra quando gli eventi devono essere attivati. Questa operazione viene eseguita per garantire che gli eventi vengono inviati al thread che ha chiamato **IConnectionPoint::** nel punto di connessione. Questa architettura può causare problemi quando il thread che deve ricevere le notifiche non pumping dei messaggi di finestra. Problemi potenziali includono gli eventi di ADO non vengono recapitati ai broadcast finestra globale scadere e possibilmente rallentare l'intero sistema perché le finestre nascoste non elaborano i messaggi e del thread. Thread STA hanno in genere un message pump di esecuzione in modo che il problema non manifestarsi sul thread STA. Thread MTA, tuttavia, in genere non ha un message pump in modo il problema si manifesta in genere in thread MTA.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [Tipi di eventi](../../../ado/guide/data/types-of-events.md)  
  
-   [Parametri evento](../../../ado/guide/data/event-parameters.md)  
  
-   [Interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [Creazione di istanze evento ADO per linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Creazione di istanze di ADO evento dal linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Parametri di evento](../../../ado/guide/data/event-parameters.md)   
 [Tipi di eventi](../../../ado/guide/data/types-of-events.md)
