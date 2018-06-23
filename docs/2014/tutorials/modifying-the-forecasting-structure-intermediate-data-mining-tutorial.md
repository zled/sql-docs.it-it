---
title: Modifica della struttura di previsione (esercitazione intermedia di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4252f9885070067278a24db266ce58714366e69b
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312129"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Modifica della struttura di previsione (Esercitazione intermedia sul data mining)
  La struttura di data mining creata nell'attività precedente contiene un singolo modello di previsione. Prima di elaborare ed esaminare il modello, è necessario alterarne leggermente la struttura e modificarne una proprietà.  
  
## <a name="modifying-the-mining-structure"></a>Modifica della struttura di data mining  
 È possibile modificare la struttura di data mining utilizzando il **struttura di Data Mining** scheda Progettazione modelli di Data Mining. Quando è stato creato il modello con Creazione guidata modello di data mining, sono state utilizzate solo tre colonne: ReportingDate, ModelRegion e Quantity. Tuttavia, il **Forecasting** tabella contiene anche una colonna quantità che è possibile usare per stimare i ricavi delle vendite. Tramite il **struttura di Data Mining** scheda, è possibile aggiungere questa colonna dalla vista origine dati alla struttura di data mining.  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>Per aggiungere la colonna Amount alla struttura di data mining Forecasting  
  
1.  Nel **struttura di Data Mining** scheda Progettazione modelli di Data Mining, nel **vista origine dati** riquadro, selezionare la colonna Amount nella tabella vTimeSeries.  
  
2.  Trascinare la colonna Amount dal **vista origine dati** riquadro nell'elenco di colonne per il **Forecasting** struttura.  
  
     La colonna Amount è ora inclusa nel **Forecasting** struttura di data mining.  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>Modifica delle colonne del modello di data mining  
 Dato che alla struttura è stata aggiunta una nuova colonna, è necessario definire in che modo la colonna verrà utilizzata dal modello. È possibile specificare come verrà usata la colonna nella **modelli di Data Mining** scheda Progettazione modelli di Data Mining.  
  
 Il **modelli di Data Mining** scheda sono elencate le colonne contenute nella struttura di data mining nel **struttura** colonna della griglia ed elenca le colonne contenenti nella colonna che contiene il nome del modello di data mining il modello, in questo caso **Forecasting**. Fare clic sui nomi delle colonne per apportare modifiche. Nel **Forecasting** modello di data mining, la colonna Amount viene utilizzata come colonna di input e viene inoltre utilizzata per stimare le vendite future. È pertanto necessario impostare le proprietà della colonna in modo che possa essere utilizzata sia come colonna di input che come colonna stimabile.  
  
> [!NOTE]  
>  Nel **modelli di Data Mining** scheda, è inoltre possibile creare nuovi modelli basati sulla stessa struttura e può modificare le proprietà di algoritmo e di colonna per ogni modello. È tuttavia necessario elaborare il modello prima che queste modifiche diventino effettive.  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>Per definire in che modo verrà utilizzata la colonna Amount  
  
1.  Nel **Forecasting** colonna della griglia nella **modelli di Data Mining** scheda, fare clic nella cella della riga Amount.  
  
2.  Selezionare **Predict** dall'elenco.  
  
     La colonna Amount è ora sia una colonna di input che una colonna stimabile.  
  
 È inoltre possibile modificare le proprietà delle singole colonne selezionando la colonna e aprendo la **proprietà** finestra. Per aprire la **delle proprietà** finestra, il nome della colonna e quindi scegliere **proprietà**. Se si modifica una proprietà di un singolo modello all'interno della colonna, è possibile modificare le proprietà solo di quel modello. Tuttavia, quando si modifica una proprietà all'interno di **struttura** colonna, la modifica influisce su tutti i modelli che sono associato alla struttura. Ogni qualvolta si apportano modifiche al modello o alla struttura, è necessario ripetere l'elaborazione per osservarne gli effetti.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Personalizzazione ed elaborazione del modello di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture di data mining &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modelli di data mining &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  