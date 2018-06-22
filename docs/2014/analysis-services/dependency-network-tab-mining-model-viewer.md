---
title: Scheda di rete di dipendenze (Visualizzatore modello di Data Mining) | Documenti Microsoft
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
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e3f8b993490c349cab5a6f25c722f83719b844af
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054655"
---
# <a name="dependency-network-tab-mining-model-viewer"></a>Scheda Rete di dipendenze (Visualizzatore modello di data mining)
  La scheda **Rete di dipendenze** consente di visualizzare graficamente tutti gli attributi contenuti nel modello di dati mining e la relativa modalità di correlazione.  
  
 La scheda **Rete di dipendenze**  viene utilizzata per diversi tipi di modelli di data mining, inclusi i modelli Naive Bayes, di albero delle decisioni e di associazione. Per ulteriori informazioni su come interpretare il contenuto della scheda **Rete di dipendenze**  nel contesto di questi modelli, vedere i collegamenti seguenti:  
  
 [Visualizzare un modello usando il Visualizzatore Microsoft Decision Trees](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [Visualizzare un modello usando il Visualizzatore Microsoft Naive Bayes](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [Visualizzare un modello usando il Visualizzatore Microsoft Association Rules](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Consente di scegliere un modello di data mining da visualizzare tra quelli presenti nella struttura di data mining corrente. Il modello di data mining verrà aperto in un visualizzatore personalizzato. Il tipo di visualizzatore personalizzato utilizzato per ogni modello viene determinato dall'algoritmo utilizzato per creare il modello.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per l'esplorazione del modello di data mining selezionato. Per ogni modello è possibile utilizzare il visualizzatore personalizzato fornito per ogni modello di data mining o Visualizzatore contenuto di data mining [!INCLUDE[msCoName](../includes/msconame-md.md)] . Se disponibili, è anche possibile utilizzare i visualizzatori plug-in. Microsoft Generic Content Tree Viewer può essere utilizzato con tutti i modelli e rappresenta il contenuto del modello in una tabella HTML.  
  
 **Eseguire lo zoom avanti**  
 Consente di eseguire lo zoom avanti del diagramma in modo da poter visualizzare più dettagliatamente gli attributi.  
  
 **Eseguire lo zoom indietro**  
 Consente di eseguire lo zoom indietro del diagramma in modo da poter visualizzare più attributi e i relativi collegamenti.  
  
 **Copia parte visibile del grafico**  
 Consente di copiare la sezione visibile del diagramma negli Appunti.  
  
 **Copia grafico intero**  
 Consente di copiare tutto il diagramma negli Appunti.  
  
 **Collegamenti**  
 Consente di impostare il numero di collegamenti (bordi) e nodi mostrati dal visualizzatore regolando l'indicatore di scorrimento a destra degli attributi. Trascinando la barra del dispositivo di scorrimento verso il basso viene aumentato il valore soglia in modo da visualizzare solo i collegamenti più attendibili. Per ogni tipo di modello, viene utilizzato un valore leggermente diverso per rappresentare i collegamenti nel grafico:  
  
-   In un modello di **albero delle decisioni** i bordi rappresentano l'attendibilità predittiva della connessione, determinata in parte dal punteggio di divisione.  
  
-   In un modello **Naive Bayes** i collegamenti tra due nodi possono andare in entrambe le direzioni, ovvero il nodo A può consentire la stima del nodo B e viceversa. Il punteggio associato al bordo rappresenta l'attendibilità predittiva della connessione.  
  
-   In un **modello di associazione**i bordi tra i nodi rappresentano il punteggio di priorità della regola tramite cui sono connessi due set di elementi.  
  
 Una regola generale per tutti i tipi di modelli prevede che maggiore è l'attendibilità del collegamento, maggiore sarà l'attendibilità della relazione predittiva tra i due attributi.  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori dei modelli di data mining &#40;progettazione modello di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  