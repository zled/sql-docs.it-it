---
title: Scheda caratteristiche (Visualizzatore modello di Data Mining) del cluster | Documenti Microsoft
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
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4e5dcac98dd53edbd5e894c639c067106288e7e1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170251"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a>Scheda Caratteristiche cluster (Visualizzatore modello di data mining)
  La scheda **Caratteristiche cluster** consente di esplorare le caratteristiche di un cluster in un modello di clustering o il set di tutti i case nel modello. Nel grafico viene mostrata l'importanza di ogni coppia attributo-valore come caratteristica tramite cui viene definito il cluster rispetto agli altri cluster.  
  
 **Per altre informazioni:** [Algoritmo Microsoft Clustering](data-mining/microsoft-clustering-algorithm.md), [Visualizzare un modello usando il Visualizzatore Microsoft Clustering](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Consente di scegliere un modello di data mining tra quelli presenti nella struttura di data mining corrente. Il modello di data mining verrà aperto nel visualizzatore personalizzato.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per l'esplorazione del modello di data mining selezionato. È possibile usare il visualizzatore personalizzato associato a questo tipo di modello o il Visualizzatore contenuto di data mining [!INCLUDE[msCoName](../includes/msconame-md.md)] . Se disponibili, è anche possibile utilizzare i visualizzatori plug-in.  
  
 **Cluster**  
 Consente di scegliere il cluster da visualizzare o **Popolazione (Tutto)** per vedere la distribuzione degli attributi per l'intero modello.  
  
 **Caratteristiche per \<cluster >**  
 Nel grafico sono contenute le colonne seguenti in cui sono descritte le caratteristiche del cluster selezionato.  
  
|valore|Description|  
|-----------|-----------------|  
|**Variabile**|Vengono elencati gli attributi del modello di data mining individuati nel cluster selezionato.|  
|**Valori**|Vengono elencati i valori degli attributi correnti individuati nel cluster attualmente selezionato.|  
|**Probabilità**|La barra indica l'attendibilità della coppia attributo-valore come caratteristica di distinzione di questo cluster. Se si posiziona il mouse sulla barra è possibile vedere il valore di probabilità rappresentato in percentuale. Con questa combinazione di attributo e valore in qualsiasi case particolare, tramite tale valore viene indicata la probabilità che il case appartenga a questo cluster.|  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori dei modelli di data mining &#40;progettazione modello di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  