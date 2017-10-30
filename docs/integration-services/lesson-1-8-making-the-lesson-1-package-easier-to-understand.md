---
title: 'Passaggio 8: Semplificazione del pacchetto della lezione 1 comprensione | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 55bd386054f3a7d066dc8c28c13e22ae82e9f0cb
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-8---making-the-lesson-1-package-easier-to-understand"></a>Lezione 1-8-rendendo più facile comprensione del pacchetto della lezione 1
Dopo avere completato la configurazione del pacchetto della lezione 1, può essere utile riordinarne il layout. Se le forme nel layout del flusso di controllo e del flusso di dati sono di dimensioni casuali o se non sono allineate o raggruppate, può risultare più difficile comprendere la funzionalità del pacchetto.  
  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools sono disponibili strumenti che consentono di formattare facilmente e rapidamente il layout dei pacchetti. Le caratteristiche di formattazione includono la possibilità di impostare forme di dimensioni uguali, di allineare le forme e di modificare la spaziatura orizzontale e verticale tra le forme.  
  
Un altro modo per rendere più comprensibili le funzionalità del pacchetto consiste nell'aggiunta di annotazioni descrittive.  
  
In questa attività verranno utilizzate le funzionalità di formattazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools per migliorare il layout del flusso di dati e aggiungere un'annotazione al flusso di dati.  
  
### <a name="to-format-the-layout-of-the-data-flow"></a>Per formattare il layout del flusso di dati  
  
1.  Se il pacchetto della lezione 1 non è aperto, fare doppio clic su Lesson 1.dtsx in Esplora soluzioni.  
  
2.  Fare clic sulla scheda **Flusso di dati** .  
  
3.  Posizionare il cursore in alto a destra rispetto alla trasformazione Extract Sample Currency, fare clic e trascinare il cursore su tutti i componenti del flusso di dati.  
  
4.  Scegliere **Rendi uguali** dal menu **Formato**e quindi fare clic su **Entrambe**.  
  
5.  Con gli oggetti del flusso di dati selezionati, scegliere **Allinea** dal menu **Formato**e quindi fare clic su **A sinistra**.  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a>Per aggiungere un'annotazione al flusso di dati  
  
1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dello sfondo dell'area di progettazione del flusso di dati e quindi scegliere **Aggiungi annotazione**.  
  
2.  Digitare o incollare il testo seguente nella casella delle annotazioni.  
  
    **Tramite il flusso di dati vengono estratti dati da un file, vengono cercati valori nella colonna CurrencyKey della tabella DimCurrency e nella colonna DateKey della tabella DimDate e vengono scritti i dati nella tabella NewFactCurrencyRate.**  
  
    Per eseguire il wrapping del testo nella casella delle annotazioni, inserire il cursore nel punto in cui si desidera iniziare una nuova riga e premere INVIO.  
  
    Se non si inserisce alcun testo nella casella delle annotazioni, quest'ultima scomparirà quando si farà clic al suo esterno.  
  
## <a name="next-steps"></a>Passaggi successivi  
[Passaggio 9: Test del pacchetto creato nella lezione 1 dell'esercitazione](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
  

