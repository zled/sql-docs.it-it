---
title: Microsoft Generic Content Tree Viewer (Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: eb48d0ce455c41f6e684b54af86bb6ff5f8eddfb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067692"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a>Microsoft Generic Content Tree Viewer (Data mining)
  In **Microsoft Generic Content Tree Viewer** vengono visualizzate informazioni dettagliate sul contenuto di un modello di data mining in un formato di tabella HTML standardizzato. Questa vista è utile poiché vengono esposti la struttura sottostante del modello, nonché i dettagli sui coefficienti, sulla distribuzione dei valori e così via.  
  
 Il contenuto effettivo visualizzato nella tabella varia a seconda dell'algoritmo utilizzato e possono essere inclusi colonne, regole, proprietà, attributi, nodi e formule. Per altre informazioni sul contenuto del modello e su come interpretare le informazioni per ogni tipo di modello, vedere [Contenuto del modello di data mining &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
 Per le informazioni fornite nel visualizzatore viene utilizzata una struttura comune basata sul set di righe dello schema relativo al contenuto per i modelli di data mining. Tale set di righe è un framework generico per l'archiviazione degli schemi, delle statistiche e di altro contenuto di un modello di data mining. Per un elenco delle colonne del set di righe dello schema di data mining per i modelli di data mining, vedere [Set di righe DMSCHEMA_MINING_MODEL_CONTENT](schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md).  
  
## <a name="options"></a>Opzioni  
 **Didascalia del nodo (ID univoco)**  
 In questo riquadro viene visualizzato un elenco di tutti i nodi nel modello di data mining selezionato. La modalità di disposizione dei nodi nell'albero è diversa a seconda del tipo di modello visualizzato.  
  
 È possibile fare clic su ogni nodo per visualizzare le relative informazioni dettagliate nel riquadro **Dettagli nodo** .  
  
 **Dettagli nodo**  
 Vengono visualizzate informazioni dettagliate sul contenuto del nodo selezionato. In ogni nodo vengono archiviate le relative informazioni in un formato standardizzato, tuttavia il contenuto e il significato di ogni riga della tabella dipendono dal tipo di modello o di nodo visualizzato. Ad esempio, le informazioni archiviate per un nodo che rappresenta una regola in un modello di associazione sono diverse rispetto a quelle di un nodo che rappresenta un albero in un modello di albero delle decisioni.  
  
 Per informazioni su come interpretare le informazioni per un tipo di modello specifico, vedere [Contenuto del modello di data mining &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori dei modelli di data mining &#40;progettazione modello di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Query di Data Mining](data-mining/data-mining-queries.md)  
  
  