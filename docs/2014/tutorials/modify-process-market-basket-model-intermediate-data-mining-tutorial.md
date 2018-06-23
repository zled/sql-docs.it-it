---
title: Modifica ed elaborazione del modello Market Basket (esercitazione intermedia di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 96eb44713cd34fdcea81a7e5e4daf26739afdec1
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311909"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>Modifica ed elaborazione del modello Market Basket (Esercitazione intermedia sul data mining)
  Prima di elaborare il modello di data mining di associazione che è stato creato, è necessario modificare i valori predefiniti dei due parametri: *supporto* e *probabilità*.  
  
-   *Supporto* definisce la percentuale di casi in cui una regola deve esistere prima che venga considerato valido. Sarà necessario specificare che la regola deve essere presente almeno nell'1% dei case.  
  
-   *Probabilità* definisce la probabilità un'associazione deve essere prima che venga considerato valido. Verrà presa in considerazione ogni associazione con almeno il 10% di probabilità.  
  
 Per ulteriori informazioni sugli effetti di aumentando o diminuendo il supporto e probabilità, vedere [riferimento tecnico l'algoritmo Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 Dopo aver definito la struttura e parametri per il **associazione** modello di data mining, sarà necessario elaborare il modello.  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>Per adattare i parametri del modello Association  
  
1.  Aprire la **modelli di Data Mining** scheda Progettazione modelli di Data Mining.  
  
2.  Fare doppio clic sui **Association** colonna della griglia nella finestra di progettazione e selezionare **imposta parametri algoritmo per aprire i parametri dell'algoritmo** finestra di dialogo.  
  
3.  Nel **valore** colonna del **i parametri dell'algoritmo** dialogo casella, impostare i parametri seguenti:  
  
     MINIMUM_PROBABILITY = 0,1  
  
     MINIMUM_SUPPORT = 0,01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>Per elaborare il modello di data mining  
  
1.  Nel **modello di Data Mining** dal menu del [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], selezionare **Elabora struttura di Data Mining e tutti i modelli.**  
  
2.  Nella finestra di avviso che chiede se si desidera compilare e distribuire il progetto, fare clic su **Sì**.  
  
     Il **Elabora struttura di Data Mining - Association** verrà visualizzata la finestra di dialogo.  
  
3.  Fare clic su **Esegui**.  
  
     Il **stato elaborazione** verrà visualizzata la finestra di dialogo per visualizzare le informazioni sull'elaborazione del modello. L'elaborazione della nuova struttura e del nuovo modello potrebbe richiedere tempo.  
  
4.  Al termine dell'elaborazione, fare clic su **Close** per uscire dall'installazione di **stato elaborazione** finestra di dialogo.  
  
5.  Fare clic su **Close** per uscire dal **Elabora struttura di Data Mining - Association** finestra di dialogo.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Esplorazione dei modelli Market Basket &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni e requisiti di elaborazione &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  