---
title: Finestra di dialogo parametri algoritmo (visualizzazione modelli di Data Mining) | Documenti Microsoft
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
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 996a6b9ad990eeccd74888c8b43cd29b12ef17db
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158325"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a>Finestra di dialogo Parametri algoritmo (visualizzazione Modelli di data mining)
  Usare la finestra di dialogo **Parametri algoritmo** per modificare i parametri dell'algoritmo specifici per il modello selezionato. Quando si modifica un parametro dell'algoritmo, i risultati del modello di data mining di solito cambiano. L'influenza che ogni parametro ha sui risultati dipende dall'algoritmo utilizzato e dai dati. Per altre informazioni, vedere [Personalizzare struttura e modelli di data mining](data-mining/customize-mining-models-and-structure.md).  
  
## <a name="options"></a>Opzioni  
 **Parametri**  
 Consente di visualizzare l'elenco dei parametri disponibili per il modello di data mining selezionato.  
  
 Di seguito vengono descritte le colonne disponibili.  
  
|colonna|Description|  
|------------|-----------------|  
|**Parametro**|Indica il nome del parametro.|  
|**Value**|Immettere un valore solo se si desidera modificare quello predefinito del parametro.|  
|**Default**|Indica il valore predefinito del parametro usato dall'algoritmo se non si specifica un valore nella colonna **Valore** .|  
|**Intervallo**|Indica l'intervallo di valori che è possibile immettere nella colonna **Valore** . Gli intervalli possono essere uno dei valori seguenti:<br /><br /> Elenco discreto, ad esempio 1, 2, 3<br /><br /> Un intervallo inclusivo, ad esempio [0, 100]<br /><br /> Intervallo esclusivo, ad esempio (0,...)<br /><br /> Una combinazione, ad esempio [0,...)|  
  
 **Descrizione**  
 Descrive il parametro selezionato nell'elenco **Parametri** .  
  
 **Aggiungi**  
 Consente di aggiungere all'elenco ulteriori parametri specifici per l'algoritmo. Dopo l'aggiunta del parametro, è possibile immetterne il nome corretto nella colonna **Parametro** e specificare un valore nella colonna **Valore** .  
  
 **Rimuovi**  
 Consente di eliminare un parametro personalizzato dall'elenco.  
  
 Se si elimina dall'elenco uno dei parametri dell'algoritmo standard di Analysis Services, il parametro verrà ancora utilizzato nel modello, ma con i valori predefiniti per quel parametro. Il parametro non è eliminato in modo permanente e verrà visualizzato la volta successiva che si apre la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzazione di modelli di data mining &#40;progettazione modello di Data Mining&#41;](mining-models-view-data-mining-model-designer.md)   
 [Spostamento di oggetti di data mining](data-mining/moving-data-mining-objects.md)  
  
  