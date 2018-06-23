---
title: Aggiunta di un modello di regressione logistica alla struttura del Call Center (esercitazione intermedia di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ccadf7665b112b6ba1055fdcf69aeb99609c3ab3
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312429"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a>Aggiunta di un modello di regressione logistica alla struttura del call center (Esercitazione intermedia sul data mining)
  Oltre ad analizzare i fattori che potrebbero influire sul funzionamento del call center, è inoltre necessario fornire alcuni consigli specifici su come il personale può migliorare la qualità del servizio. In questa attività verrà utilizzata la stessa struttura di data mining utilizzata per compilare il modello esplorativo e verrà aggiunto un modello di data mining che sarà utilizzato per la creazione di stime.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] un modello di regressione logistica è basato sull'algoritmo Microsoft Neural Network e pertanto fornisce la stessa flessibilità e le funzionalità di un modello di rete neurale. La regressione logistica è tuttavia particolarmente appropriata per stimare risultati binari.  
  
 Per questo scenario si utilizzerà la stessa struttura di data mining utilizzata per il modello di rete neurale. Il nuovo modello verrà tuttavia personalizzato per soddisfare le esigenze aziendali. Si desidera migliorare la qualità del servizio e determinare quanti operatori esperti sono necessari, pertanto si configurerà il modello per stimare tali valori.  
  
 Per assicurarsi che i tutti i modelli basati sui dati del call center siano il più possibile simili, si utilizzerà lo stesso valore di inizializzazione precedente. L'impostazione del parametro del valore di inizializzazione assicura che il modello elabori i dati dallo stesso punto iniziale e riduca le variazioni causate dagli elementi nei dati.  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a>Per aggiungere un nuovo modello di data mining alla struttura di data mining del call center  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni fare doppio clic su struttura di data mining **Call Center Binned**e selezionare **Apri finestra di progettazione**.  
  
2.  Progettazione modelli di Data Mining, fare clic sui **modelli di Data Mining** scheda.  
  
3.  Fare clic su **creare un modello di data mining correlato**.  
  
4.  Nel **nuovo modello di Data Mining** della finestra di dialogo per **Model name**, tipo `Call Center - LR`.  Per **nome dell'algoritmo**, selezionare **Microsoft Logistic Regression**.  
  
5.  Fare clic su **OK**.  
  
     Il nuovo modello di data mining viene visualizzato nel **modelli di Data Mining** scheda.  
  
### <a name="to-customize-the-logistic-regression-model"></a>Per personalizzare il modello di regressione logistica  
  
1.  Nella colonna per il nuovo modello di data mining, `Call Center - LR`, lasciare Fact CallCenter ID come chiave.  
  
2.  Modificare il valore di ServiceGrade e Level Two Operators in **Predict**.  
  
     Queste colonne verranno utilizzate sia per la stima che per l'input. In sostanza, si creano due modelli separati basati sugli stessi dati: uno che stima il numero di operatori e uno che stima il livello di servizio.  
  
3.  Modificare tutte le altre colonne per **Input**.  
  
### <a name="to-specify-the-seed-and-process-the-models"></a>Per specificare il valore di inizializzazione ed elaborare i modelli  
  
1.  Nel **modello di Data Mining** scheda, la colonna per il modello denominato Call Center - LR e scegliere **imposta parametri algoritmo**.  
  
2.  Nella riga del parametro HOLDOUT_SEED, fare clic sulla cella vuota sotto **valore**e il tipo `1`. Fare clic su **OK**.  
  
    > [!NOTE]  
    >  Il valore scelto come valore di inizializzazione non è importante, a condizione che si utilizzi lo stesso valore di inizializzazione per tutti i modelli correlati.  
  
3.  Nel **modelli di Data Mining** dal menu **Elabora struttura di Data Mining e tutti i modelli**. Fare clic su **Sì** per distribuire il progetto di data mining i dati aggiornati nel server.  
  
4.  Nel **modello di processo di Data Mining** finestra di dialogo, fare clic su **eseguire**.  
  
5.  Fare clic su **chiudere** per chiudere il **stato elaborazione** finestra di dialogo e quindi fare clic su **chiudere** nuovamente il **modello di Data Mining processo** finestra di dialogo.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Creazione di stime per i modelli Call Center &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni e requisiti di elaborazione &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  