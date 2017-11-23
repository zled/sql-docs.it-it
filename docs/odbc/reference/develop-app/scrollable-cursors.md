---
title: I cursori scorrevoli | Documenti Microsoft
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
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 2c8a5f50-9b37-452f-8160-05f42bc4d97e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f926f312b1696b3fcc3433e6234dc0f44005b7cf
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="scrollable-cursors"></a>Cursori scorrevoli
Nelle applicazioni moderne basate su schermo, l'utente scorre avanti e indietro i dati. Per tali applicazioni, la restituzione di una riga recuperata in precedenza è un problema. Una possibilità consiste nel chiudere e riaprire il cursore e quindi recuperare le righe finché il cursore raggiunge la riga necessaria. Un'altra possibilità consiste nel leggere il set di risultati, memorizzarlo nella cache in locale e implementare lo scorrimento nell'applicazione. Entrambe le possibilità funzionano bene solo con set di risultati di piccole dimensioni e la possibilità di quest'ultima è difficile da implementare. Una soluzione migliore consiste nell'utilizzare un *con cursori scorrevoli,* che può spostarsi avanti e indietro nel set di risultati.  
  
 Oggetto *cursore scorrevole* viene in genere utilizzato nelle applicazioni moderne basate su schermo in cui l'utente scorre avanti e indietro i dati. Tuttavia, le applicazioni utilizzino i cursori scorrevoli solo quando i cursori forward-only non eseguirà il processo, come i cursori scorrevoli risultano in genere è più costosi di cursori forward-only.  
  
 La possibilità di spostarsi all'indietro genera una domanda non applicabile per i cursori forward-only: deve un cursore scorrevole rilevare le modifiche apportate alle righe precedentemente recuperate? Vale a dire, deve rilevare le righe aggiornate, eliminate e appena inserite?  
  
 Questa domanda si verifica perché la definizione di un risultato impostata, il set di righe che soddisfa determinati criteri, non indicano quando le righe vengono controllate per verificare se corrispondono ai criteri di tale né stato se righe devono contenere gli stessi dati ogni volta che vengono richiamate. L'omissione precedente rende possibile per i cursori scorrevoli rilevare se le righe sono state inserite o eliminate, mentre quest'ultimo consente di rilevare i dati aggiornati.  
  
 La possibilità di rilevare le modifiche è talvolta utile, in alcuni casi non. Ad esempio, un'applicazione di contabilità richiede un cursore che ignora tutte le modifiche; documentazione di bilanciamento del carico è possibile eseguire se il cursore mostra le modifiche più recenti. D'altra parte, un sistema di prenotazione airline necessita di un cursore che visualizza le ultime modifiche apportate ai dati; senza un cursore, è necessario requery continuamente il database per visualizzare la disponibilità di volo più aggiornata.  
  
 Per soddisfare le esigenze delle diverse applicazioni, ODBC definisce quattro diversi tipi di cursori scorrevoli. Questi cursori variano entrambe in costi e impostato per la capacità di rilevare le modifiche apportate al risultato. Si noti che se un cursore scorrevole può rilevare le modifiche alle righe, è possibile solo in grado di rilevarli durante il tentativo di recupero di tali righe. non è possibile per l'origine dati per notificare al cursore le modifiche apportate alle righe attualmente recuperate. Si noti inoltre che la visibilità delle modifiche è controllata anche dal livello di isolamento delle transazioni; Per ulteriori informazioni, vedere [isolamento delle transazioni](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di cursore scorrevoli](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Utilizzo di cursori scorrevoli](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Scorrimento relativo e assoluto](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Segnalibri](../../../odbc/reference/develop-app/bookmarks-odbc.md)
