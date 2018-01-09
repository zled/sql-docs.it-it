---
title: Recupero di dati tramite il set di celle | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- CellSet object
- retrieving data
- data retrieval [ADOMD.NET], CellSet object
ms.assetid: 77e4ee58-882d-4012-91a3-0565f18a4882
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e1552ce0646c48465aac824f40d9f42f8aa4215d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="retrieving-data-using-the-cellset"></a>Recupero di dati tramite l'oggetto CellSet
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Durante il recupero dei dati analitici, la <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> oggetto fornisce più funzionalità di interattività e flessibilità. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> è costituito da una cache in memoria di dati e metadati gerarchici che mantiene la dimensionalità originale dei dati. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> può inoltre trovarsi in uno stato connesso o disconnesso. Grazie alla disponibilità della modalità disconnessa, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> può essere utilizzato per visualizzare dati e metadati in qualsiasi ordine e fornisce il modello a oggetti più completo per il recupero dei dati. A causa della possibilità di essere utilizzato anche in modalità disconnessa, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> è caratterizzato tuttavia dall'overhead maggiore e rappresenta il modello a oggetti per il recupero dei dati di ADOMD.NET più lento da popolare.  
  
## <a name="retrieving-data-in-a-connected-state"></a>Recupero di dati in uno stato connesso  
 Per utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> per recuperare dati, effettuare le seguenti operazioni:  
  
1.  **Creare una nuova istanza dell'oggetto.**  
  
     Per creare una nuova istanza dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Identificare i metadati.**  
  
     Oltre a recuperare dati, ADOMD.NET recupera anche i metadati per il set di celle. Non appena il comando ha eseguito la query e ha restituito un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, è possibile recuperare i metadati tramite i vari oggetti. Tali metadati sono necessari affinché le applicazioni client visualizzino e interagiscano con i dati del set di celle. Molte applicazioni client ad esempio consentono di eseguire il drill-down o di visualizzare gerarchicamente le posizioni figlio di una posizione specificata in un set di celle.  
  
     In ADOMD.NET le proprietà <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Axes%2A> e <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.FilterAxis%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> rappresentano i metadati degli assi di query e di sezionamento, rispettivamente, nel set di celle restituito. Entrambe le proprietà restituiscono riferimenti a oggetti <xref:Microsoft.AnalysisServices.AdomdClient.Axis> che a loro volta contengono le posizioni rappresentate su ogni asse.  
  
     Ogni oggetto <xref:Microsoft.AnalysisServices.AdomdClient.Axis> contiene una raccolta di oggetti <xref:Microsoft.AnalysisServices.AdomdClient.Position> che rappresentano il set di tuple disponibili per l'asse specifico. Ogni oggetto <xref:Microsoft.AnalysisServices.AdomdClient.Position> rappresenta una singola tupla che contiene uno o più membri, rappresentati da una raccolta di oggetti <xref:Microsoft.AnalysisServices.AdomdClient.Member>.  
  
3.  **Recuperare i dati dalla raccolta di set di celle.**  
  
     Oltre a recuperare metadati, ADOMD.NET recupera anche i dati per il set di celle. Non appena il comando ha eseguito la query e ha restituito un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, è possibile recuperare i dati tramite la raccolta <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>. Poiché tale raccolta contiene i valori calcolati per l'intersezione di tutti gli assi nella query, sono presenti diversi indicizzatori per accedere a ogni intersezione o cella. Per un elenco di indicizzatori, vedere <xref:Microsoft.AnalysisServices.AdomdClient.CellCollection.Item%2A>.  
  
### <a name="example-of-retrieving-data-in-a-connected-state"></a>Esempio di recupero di dati in uno stato connesso  
 Nell'esempio seguente viene stabilita una connessione al server locale, quindi viene eseguito un comando nella connessione. Nell'esempio vengono analizzati i risultati utilizzando il **set di celle** modello a oggetti: le didascalie (metadati) per le colonne vengono recuperate dal primo asse e le didascalie (metadati) per ogni riga vengono recuperate dal secondo asse e l'intersezione di dati vengono recuperati utilizzando il <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A> insieme.  
  
 [!code-cs[Adomd.NetClient#ReturnCommandUsingCellSet](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-data-using-th_0_1.cs)]  
  
## <a name="retrieving-data-in-a-disconnected-state"></a>Recupero di dati in uno stato disconnesso  
 Caricando il codice XML restituito da una query precedente, è possibile utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> per disporre di un metodo completo per l'esplorazione di dati analitici senza che sia necessario stabilire una connessione attiva.  
  
> [!NOTE]  
>  Non tutte le proprietà disponibili dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> lo sono nel caso in cui lo stato sia disconnesso. Per ulteriori informazioni, vedere <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>.  
  
### <a name="example-of-retrieving-data-in-a-disconnected-state"></a>Esempio di recupero di dati in uno stato disconnesso  
 L'esempio seguente è analogo a quello relativo ai metadati e ai dati illustrato in precedenza in questo argomento. Tuttavia, il comando nell'esempio seguente viene eseguita con una chiamata a <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>, e il risultato viene restituito come un **causerebbe**. Nell'esempio viene quindi popola il <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> oggetto utilizzando questo **causerebbe** con il <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A> metodo. Sebbene questo esempio viene caricato il **causerebbe** immediatamente, è possibile memorizzare nella cache il codice XML contenuto dal lettore in un disco rigido o trasmettere tali dati a un'applicazione diversa con qualunque strumento prima di caricare i dati in un set di celle.  
  
 [!code-cs[Adomd.NetClient#DemonstrateDisconnectedCellset](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-data-using-th_0_2.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di dati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)   
 [Recupero di dati tramite AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)   
 [Recupero di dati tramite XmlReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)  
  
  
