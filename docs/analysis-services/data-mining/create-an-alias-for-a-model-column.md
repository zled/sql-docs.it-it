---
title: Creare un Alias per una colonna del modello | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c08cce1946d46d4d0d5837f4983e9e773a87c746
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="create-an-alias-for-a-model-column"></a>Creare un alias per una colonna di un modello
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] è possibile creare un alias per una colonna di un modello. Questa funzione può risultare utile quando il nome della struttura di data mining è troppo lungo o quando si desidera scegliere un nome più descrittivo del contenuto della colonna o del relativo utilizzo nel modello. Se ad esempio si crea una copia di una colonna di una struttura e quindi si discretizza la colonna in modo diverso per un determinato modello, è possibile rinominarla per riflettere più accuratamente il contenuto.  
  
 Per creare un alias per una colonna di un modello, usare il riquadro **Proprietà** e impostare la proprietà [Name](../../analysis-services/scripting/properties/name-element-assl.md) della colonna.  
  
 Nella scheda **Modelli di data mining** di Progettazione data mining l'alias viene visualizzato racchiuso tra parentesi accanto all'etichetta di utilizzo della colonna.  
  
 Per informazioni su come impostare le proprietà di un modello di data mining, vedere [Colonne del modello di data mining](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Per aggiungere un alias a una colonna di un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla cella del modello di data mining per la colonna che si vuole modificare e quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** sul lato destro dello schermo fare clic sulla cella accanto alla proprietà Name ed eliminare il valore corrente. Digitare un nuovo nome per la colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività di modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Proprietà modello di data mining](../../analysis-services/data-mining/mining-model-properties.md)  
  
  
