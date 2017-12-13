---
title: Elabora un modello di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ef9aab1e5608be6c9b06401e05ebfa6df9cee8c7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="process-a-mining-model"></a>Elaborare un modello di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Nella scheda modelli di Data Mining di progettazione Data Mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consente di elaborare un modello di data mining specifico associato a una struttura di data mining o è possibile elaborare tutti i modelli associati con la struttura.  
  
 È possibile elaborare un modello di data mining utilizzando gli strumenti seguenti:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 Inoltre, è possibile utilizzare un comando di elaborazione XMLA. Per altre informazioni, vedere [Strumenti e approcci per l’elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a>Elaborare un singolo modello di data mining utilizzando SQL Server Data Tools  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining selezionare un modello di data mining in una o più colonne di modelli nella griglia.  
  
2.  Scegliere **Elabora modello** dal menu **Modello di data mining**.  
  
     Se sono state apportate modifiche alla struttura di data mining, prima di elaborare il modello verrà richiesto di ridistribuire la struttura. Scegliere **Sì**.  
  
3.  Nel **Elaboramodello di Data Mining - \<modello >** la finestra di dialogo, fare clic su **eseguire**.  
  
     Verrà visualizzata la finestra di dialogo **Stato elaborazione** contenente informazioni sull'elaborazione dei modelli.  
  
4.  Al termine dell'elaborazione del modello, fare clic su **Chiudi** nella finestra di dialogo **Stato elaborazione** .  
  
5.  Fare clic su **Chiudi** nel **Elaboramodello di Data Mining - \<modello >** la finestra di dialogo.  
  
 Tramite questa procedura sono stati elaborati solo la struttura di data mining e il modello di data mining associato.  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a>Elaborare tutti i modelli di data mining associati a una struttura di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining scegliere **Elabora struttura di data mining e tutti i modelli** dal menu **Modello di data mining** .  
  
2.  Se sono state apportate modifiche alla struttura di data mining, prima di elaborare i modelli verrà richiesto di ridistribuire la struttura. Scegliere **Sì**.  
  
3.  Nel **struttura di Data Mining elaborazione - \<struttura >** la finestra di dialogo, fare clic su **eseguire**.  
  
4.  Verrà visualizzata la finestra di dialogo **Stato elaborazione** contenente informazioni sull'elaborazione dei modelli.  
  
5.  Al termine dell'elaborazione dei modelli, fare clic su **Chiudi** nella finestra di dialogo **Stato elaborazione** .  
  
6.  Fare clic su **Chiudi** nel **elaborazione \<modello >** la finestra di dialogo.  
  
 Tramite questa procedura sono stati elaborati la struttura di data mining e tutti i modelli di data mining associati.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
