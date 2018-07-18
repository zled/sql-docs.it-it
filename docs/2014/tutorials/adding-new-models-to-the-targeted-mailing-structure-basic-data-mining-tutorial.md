---
title: Aggiunta di nuovi modelli alla struttura Targeted Mailing (esercitazione di base di Data Mining) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
caps.latest.revision: 45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: db935cec3d17815d0884b1f596e870f6d09d5086
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222611"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Aggiunta di nuovi modelli alla struttura Targeted Mailing (Esercitazione di base sul data mining)
  In questa attività verranno definiti due modelli aggiuntivi utilizzando la **modelli di Data Mining** scheda della finestra di progettazione modelli di Data Mining. Per creare i modelli, verranno utilizzati gli algoritmi Microsoft Clustering e Microsoft Naive Bayes, per la loro capacità di stimare un valore discreto (ad esempio, l'acquisto di una bicicletta). Per altre informazioni su questi algoritmi, vedere [algoritmo Microsoft Clustering](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) e [all'algoritmo Microsoft Naive Bayes](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)  
  
### <a name="to-create-a-clustering-mining-model"></a>Per creare un modello di data mining Clustering  
  
1.  Passare al **modelli di Data Mining** della scheda Progettazione modelli di Data Mining in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
     Si noti che la finestra di progettazione vengono visualizzate due colonne, una struttura di data mining e una per il `TM_Decision_Tree` modello di data mining, che è stato creato nella lezione precedente.  
  
2.  Fare doppio clic il **struttura** colonna e selezionare **nuovo modello di Data Mining**.  
  
3.  Nel **nuovo modello di Data Mining** nella finestra di dialogo **Model name**, tipo `TM_Clustering`.  
  
4.  Nelle **nome dell'algoritmo**, selezionare **Microsoft Clustering**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Il nuovo modello verrà visualizzato nei **modelli di Data Mining** scheda della finestra di progettazione modelli di Data Mining. Questo modello, compilato con la [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo di Clustering Raggruppa i clienti con caratteristiche simili in cluster e consente di stimare bike all'acquisto per ogni cluster. Sebbene sia possibile modificare l'utilizzo delle colonne e le proprietà per il nuovo modello, non sono consentite modifiche il `TM_Clustering` modello sono necessarie per questa esercitazione.  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>Per creare un modello di data mining Naive Bayes  
  
1.  Nel **modelli di Data Mining** della scheda Progettazione modelli di Data Mining destra clickthe **struttura** colonna e selezionare **nuovo modello di Data Mining**.  
  
2.  Nel **nuovo modello di Data Mining** nella finestra di dialogo **Model name**, tipo `TM_NaiveBayes`.  
  
3.  Nelle **nome dell'algoritmo**, selezionare **Microsoft Naive Bayes**, quindi fare clic su **OK**.  
  
     Viene visualizzato un messaggio che informa che il [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo Naive Bayes non supporta la **Age** e **Yearly Income** colonne, che sono continue.  
  
4.  Fare clic su **Sì** per riconoscere il messaggio e continuare.  
  
 Verrà visualizzato un nuovo modello i **modelli di Data Mining** scheda della finestra di progettazione modelli di Data Mining. Sebbene sia possibile modificare l'utilizzo delle colonne e le proprietà per tutti i modelli in questa scheda, senza modificare il `TM_NaiveBayes` modello sono necessarie per questa esercitazione.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Elaborazione dei modelli nella struttura di Mailing diretto &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere modelli di Data Mining a una struttura &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [Progettazione modelli di Data Mining](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Spostamento di oggetti di data mining](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
