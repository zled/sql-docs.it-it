---
title: Specifica un Set di dati di Testing per la struttura (esercitazione di base di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2023672b21e8ffde191b400329031895d200e1ea
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312629"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a>Specifica di un set di dati di testing per la struttura (Esercitazione di base sul data mining)
  Nelle schermate finali della Creazione guidata modello di data mining si suddivideranno i dati in un set di testing e un set di training. Si assegnerà quindi un nome alla struttura e si abiliterà il drill-through sul modello.  
  
## <a name="specifying-a-testing-set"></a>Specifica di un set di testing  
 La separazione dei dati in set di training e set di testing durante la creazione di una struttura di data mining consente di determinare facilmente l'accuratezza dei modelli di data mining che verranno creati successivamente. Per ulteriori informazioni sui set di testing, vedere [Training e Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-specify-the-testing-set"></a>Per specificare il set di testing  
  
1.  Nel **crea Set di Testing** pagina per **percentuale di dati per il testing**, lasciare il valore predefinito di `30`.  
  
2.  Per **il numero massimo di case nel set di dati**, tipo `1000`.  
  
3.  Scegliere **Avanti**.  
  
## <a name="specifying-drillthrough"></a>Specifica del drill-through  
 Il drill-through può essere abilitato sui modelli e sulle strutture. La casella di controllo in questa finestra di dialogo abilita il drill-through nel modello denominato. Dopo l'elaborazione del modello sarà possibile recuperare le informazioni dettagliate dai dati di training utilizzati per creare il modello.  
  
 Se anche la struttura di data mining sottostante è stata configurata per consentire il drill-through, è possibile recuperare informazioni dettagliate dai case del modello e dalla struttura di data mining, comprese le colonne non incluse nel modello di data mining. Per altre informazioni, vedere [Query drill-through &#40;Data mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a>Per assegnare un nome al modello e alla struttura e specificare il drill-through  
  
1.  Nel **Completamento procedura guidata** nella pagina **nome struttura di Data Mining**, tipo `Targeted Mailing`.  
  
2.  In **nome del modello di Data Mining**, tipo `TM_Decision_Tree`.  
  
3.  Selezionare il **Consenti drill-through** casella di controllo.  
  
4.  Rivedere le **anteprima** riquadro. Si noti che solo le colonne selezionate come **chiave**, **Input** oppure **stimabile** vengono visualizzati. Le altre colonne selezionate (ad esempio, AddressLine1) non vengono utilizzate per la compilazione del modello, ma saranno disponibili nella struttura sottostante e possono essere sottoposte a query una volta che il modello viene elaborato e distribuito.  
  
5.  Fare clic su **Fine**.  
  
## <a name="previous-task-in-lesson"></a>Attività precedente della lezione  
 [Specifica il tipo di dati e il tipo di contenuto &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 3: Aggiunta e l'elaborazione di modelli](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Consenti drill-through per un modello di Data Mining](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)   
 [Query drill-through &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Specificare i dati di Training &#40;Creazione guidata di Data Mining&#41;](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  