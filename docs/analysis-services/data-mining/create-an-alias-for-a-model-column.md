---
title: Creare un Alias per una colonna del modello | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3fb8563f838908d0c2b1b5fa2d5b049d7c630b19
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="create-an-alias-for-a-model-column"></a>Creare un alias per una colonna di un modello
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è possibile creare un alias per una colonna del modello. Questa funzione può risultare utile quando il nome della struttura di data mining è troppo lungo o quando si desidera scegliere un nome più descrittivo del contenuto della colonna o del relativo utilizzo nel modello. Se ad esempio si crea una copia di una colonna di una struttura e quindi si discretizza la colonna in modo diverso per un determinato modello, è possibile rinominarla per riflettere più accuratamente il contenuto.  
  
 Per creare un alias per una colonna di un modello, usare il riquadro **Proprietà** e impostare la proprietà [Name](../../analysis-services/scripting/properties/name-element-assl.md) della colonna.  
  
 Nella scheda **Modelli di data mining** di Progettazione data mining l'alias viene visualizzato racchiuso tra parentesi accanto all'etichetta di utilizzo della colonna.  
  
 Per informazioni su come impostare le proprietà di un modello di data mining, vedere [Colonne del modello di data mining](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Per aggiungere un alias a una colonna di un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla cella del modello di data mining per la colonna che si vuole modificare e quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** sul lato destro dello schermo fare clic sulla cella accanto alla proprietà Name ed eliminare il valore corrente. Digitare un nuovo nome per la colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Proprietà dei modelli di data mining](../../analysis-services/data-mining/mining-model-properties.md)  
  
  
