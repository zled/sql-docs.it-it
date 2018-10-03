---
title: Modificare la discretizzazione di una colonna in un modello di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b5d62d42eca06775c289e4b81485e0ee7046afbc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077301"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>Modificare la discretizzazione di una colonna in un modello di data mining
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] la discretizzazione dei dati avviene in modo automatico, ciò significa che in determinati scenari i dati vengono inseriti in colonne numeriche. Se, ad esempio, i dati includono dati numerici continui e si crea un modello di albero delle decisioni, ogni colonna di dati continui verrà automaticamente inserita in contenitori, a seconda della distribuzione dei dati. Se si desidera determinare il metodo di discretizzazione dei dati, è necessario modificare le proprietà nella colonna della struttura di data mining che controlla la modalità di utilizzo dei dati del modello.  
  
 Per informazioni generali su come impostare le proprietà in un modello di data mining, vedere [Colonne del modello di data mining](mining-model-columns.md).  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>Per visualizzare le proprietà per una colonna del modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sull'intestazione di colonna che contiene il nome del modello di data mining o sulla riga della griglia che contiene il nome dell'algoritmo di data mining, quindi scegliere **Proprietà**.  
  
     Nella finestra **Proprietà** vengono visualizzate le proprietà associate all'intero modello di data mining.  
  
2.  Nella colonna **Struttura** a sinistra dello schermo fare clic sulla colonna contenente i dati numerici continui che si desidera discretizzare.  
  
     La finestra **Proprietà** viene modificata per visualizzare solo le proprietà associate alla colonna.  
  
### <a name="to-change-the-discretization-method"></a>Per modificare il metodo di discretizzazione  
  
1.  Nel **proprietà di Data Mining** fare clic sulla casella di testo accanto a **contenuto**e selezionare `Discretized` nell'elenco a discesa.  
  
     Nella finestra <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> sono ora abilitate.  
  
2.  Nel **delle proprietà** fare clic sulla casella di testo accanto a <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> e selezionare uno dei valori seguenti: `Automatic`, `EqualAreas`, o `Cluster`.  
  
    > [!NOTE]  
    >  Se l'utilizzo della colonna è impostata su `Ignore`, il **proprietà** finestra per la colonna è vuota.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
3.  Nella scheda **Proprietà** fare clic sulla casella di testo accanto a <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> e digitare un valore numerico.  
  
    > [!NOTE]  
    >  Se si modificano queste proprietà, è necessario rielaborare la struttura, insieme ai modelli che dovranno utilizzare la nuova impostazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](mining-model-tasks-and-how-tos.md)  
  
  
