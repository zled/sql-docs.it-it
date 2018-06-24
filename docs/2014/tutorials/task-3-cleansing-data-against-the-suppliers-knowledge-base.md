---
title: 'Attività 3: Pulizia dei dati rispetto alla Knowledge Base Suppliers | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ca1a98045bd9f0ee9dfc52eafb274d5698195d68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063227"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a>Attività 3: Pulizia dei dati fornitore rispetto alla Knowledge Base Suppliers
  In questa attività viene eseguito il processo di pulizia computerizzato. In DQS vengono utilizzati algoritmi e livelli di probabilità avanzati basati sui valori soglia specificati per analizzare i dati rispetto alla Knowledge Base selezionata e procedere quindi alla relativa pulizia. Vedere [informazioni pulizia dei dati tramite DQS (interna)](http://msdn.microsoft.com/library/hh213061.aspx) per altri dettagli.  
  
1.  Fare clic su **avviare** per avviare il processo di pulizia computerizzato.  
  
     ![Pagina del processo di pulizia Pulisci](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "pulire pagina del processo di pulizia")  
  
2.  Quando viene completato il processo di pulizia, esaminare **statistiche** nel **Profiler** scheda. Nelle statistiche origine è disponibile il numero di record elaborati, nonché di quelli rilevati corretti, che vengono corretti da DQS, per cui vengono suggerite modifiche da DQS e non validi. Nella casella di riepilogo a destra è possibile visualizzare i valori corretti, quelli suggeriti, nonché la completezza (l'entità della presenza dei dati) e l'accuratezza (la misura entro cui i dati possono essere utilizzati per gli scopi previsti) dei valori per ogni dominio interessato dal processo di pulizia.  
  
     ![Risultati della pulizia](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "risultati della pulizia")  
  
3.  Fare clic su **successivo** per passare alla **Gestisci e Visualizza risultati** pagina.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 4: Gestione e visualizzazione dei risultati](../../2014/tutorials/task-4-manaing-and-viewing-results.md)  
  
  