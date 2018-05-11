---
title: Rimuovere le colonne da una struttura di Data Mining | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df3e6998e4cf3b741c5181fb0c554c40abb21a32
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="remove-columns-from-a-mining-structure"></a>Rimuovere colonne da una struttura di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile utilizzare Progettazione modelli di data mining per rimuovere le colonne da una struttura di data mining dopo averla creata. I motivi per cui rimuovere una colonna della struttura di data mining possono includere i seguenti:  
  
-   La struttura di data mining contiene più copie di una colonna e si desidera evitare l'utilizzo di dati duplicati in un modello.  
  
-   I dati devono essere protetti, ma il drill-through è abilitato.  
  
-   I dati non vengono utilizzati nella modellazione e non devono essere elaborati.  
  
 L'eliminazione di una colonna dalla struttura di data mining non comporta la modifica della colonna nella vista origine dati o nei dati esterni. Solo i metadati vengono eliminati. Tuttavia, quando si modificano le colonne utilizzate in una struttura di data mining, è necessario rielaborare la struttura e alcuni modelli basati su di essa.  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>Per rimuovere una colonna dalla struttura di data mining  
  
1.  Selezionare la scheda **Struttura di data mining** in Progettazione modelli di data mining.  
  
2.  Espandere l'albero per visualizzare tutte le colonne della struttura di data mining.  
  
3.  Fare clic con il pulsante destro del mouse sulla colonna che si desidera eliminare, quindi scegliere **Elimina**.  
  
4.  Nella finestra di dialogo **Elimina oggetti** fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Data mining struttura attività e procedure](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
