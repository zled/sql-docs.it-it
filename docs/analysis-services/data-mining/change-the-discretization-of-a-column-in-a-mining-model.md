---
title: Modificare la discretizzazione di una colonna in un modello di Data Mining | Documenti Microsoft
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
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1ff56c5becadbffef1943cd47d48ccbfedd0ac99
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>Modificare la discretizzazione di una colonna in un modello di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discretizza automaticamente i valori, vale a dire i dati inseriti in colonne numeriche, in determinati scenari. Se, ad esempio, i dati includono dati numerici continui e si crea un modello di albero delle decisioni, ogni colonna di dati continui verrà automaticamente inserita in contenitori, a seconda della distribuzione dei dati. Se si desidera determinare il metodo di discretizzazione dei dati, è necessario modificare le proprietà nella colonna della struttura di data mining che controlla la modalità di utilizzo dei dati del modello.  
  
 Per informazioni generali su come impostare le proprietà in un modello di data mining, vedere [Colonne del modello di data mining](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>Per visualizzare le proprietà per una colonna del modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sull'intestazione di colonna che contiene il nome del modello di data mining o sulla riga della griglia che contiene il nome dell'algoritmo di data mining, quindi scegliere **Proprietà**.  
  
     Nella finestra **Proprietà** vengono visualizzate le proprietà associate all'intero modello di data mining.  
  
2.  Nella colonna **Struttura** a sinistra dello schermo fare clic sulla colonna contenente i dati numerici continui che si desidera discretizzare.  
  
     La finestra **Proprietà** viene modificata per visualizzare solo le proprietà associate alla colonna.  
  
### <a name="to-change-the-discretization-method"></a>Per modificare il metodo di discretizzazione  
  
1.  Nella finestra **Proprietà data mining** fare clic sulla casella di testo accanto a **Contenuto**, quindi selezionare **Discretized** nell'elenco a discesa.  
  
     Nella finestra <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> sono ora abilitate.  
  
2.  Nella scheda **Proprietà** fare clic sulla casella di testo accanto a <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> e selezionare uno dei valori seguenti: **Automatic**, **EqualAreas**o **Cluster**.  
  
    > [!NOTE]  
    >  Se l'uso della colonna è impostato su **Ignore**, la finestra **Proprietà** per la colonna è vuota.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
3.  Nella scheda **Proprietà** fare clic sulla casella di testo accanto a <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> e digitare un valore numerico.  
  
    > [!NOTE]  
    >  Se si modificano queste proprietà, è necessario rielaborare la struttura, insieme ai modelli che dovranno utilizzare la nuova impostazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
