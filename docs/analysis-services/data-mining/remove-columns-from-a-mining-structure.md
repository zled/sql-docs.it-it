---
title: Rimuovere le colonne da una struttura di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4fc6781554893147c9f2e5d1c3eb74c3526ec878
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="remove-columns-from-a-mining-structure"></a>Rimuovere colonne da una struttura di data mining
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
 [Attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
