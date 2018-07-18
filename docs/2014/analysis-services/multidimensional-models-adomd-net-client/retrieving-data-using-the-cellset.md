---
title: Il recupero dei dati tramite l'oggetto CellSet | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- CellSet object
- retrieving data
- data retrieval [ADOMD.NET], CellSet object
ms.assetid: 77e4ee58-882d-4012-91a3-0565f18a4882
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 69e53cab56cf22d6627fd8039e6a46735d934ca7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178898"
---
# <a name="retrieving-data-using-the-cellset"></a>Recupero di dati tramite l'oggetto CellSet
  Nel recupero di dati analitici, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> fornisce il livello più elevato di interattività e flessibilità. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> è costituito da una cache in memoria di dati e metadati gerarchici che mantiene la dimensionalità originale dei dati. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> può inoltre trovarsi in uno stato connesso o disconnesso. Grazie alla disponibilità della modalità disconnessa, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> può essere utilizzato per visualizzare dati e metadati in qualsiasi ordine e fornisce il modello a oggetti più completo per il recupero dei dati. A causa della possibilità di essere utilizzato anche in modalità disconnessa, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> è caratterizzato tuttavia dall'overhead maggiore e rappresenta il modello a oggetti per il recupero dei dati di ADOMD.NET più lento da popolare.  
  
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
 Nell'esempio seguente viene stabilita una connessione al server locale, quindi viene eseguito un comando nella connessione. Nell'esempio vengono analizzati i risultati tramite il modello a oggetti `CellSet`. Le didascalie (metadati) per le colonne vengono recuperate dal primo asse, mentre le didascalie (metadati) per ogni riga vengono recuperate dal secondo asse e i dati di intersezione vengono recuperati tramite la raccolta <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A>.  
  
 [!code-csharp[Adomd.NetClient#ReturnCommandUsingCellSet](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#returncommandusingcellset)]  
  
## <a name="retrieving-data-in-a-disconnected-state"></a>Recupero di dati in uno stato disconnesso  
 Caricando il codice XML restituito da una query precedente, è possibile utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> per disporre di un metodo completo per l'esplorazione di dati analitici senza che sia necessario stabilire una connessione attiva.  
  
> [!NOTE]  
>  Non tutte le proprietà disponibili dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> lo sono nel caso in cui lo stato sia disconnesso. Per altre informazioni, vedere <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>.  
  
### <a name="example-of-retrieving-data-in-a-disconnected-state"></a>Esempio di recupero di dati in uno stato disconnesso  
 L'esempio seguente è analogo a quello relativo ai metadati e ai dati illustrato in precedenza in questo argomento. Nell'esempio seguente tuttavia il comando viene eseguito con una chiamata a <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> e il risultato viene restituito come `System.Xml.XmlReader`. Successivamente nell'esempio l'oggetto viene popolato <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> con tale `System.Xml.XmlReader` tramite il metodo <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>. Anche se in questo esempio `System.Xml.XmlReader` viene caricato immediatamente, è possibile memorizzare nella cache il codice XML contenuto dal lettore in un disco rigido o trasmettere tali dati a un'applicazione diversa con qualunque strumento prima di caricare i dati in un set di celle.  
  
 [!code-csharp[Adomd.NetClient#DemonstrateDisconnectedCellset](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#demonstratedisconnectedcellset)]  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di dati da un'origine dati analitici](retrieving-data-from-an-analytical-data-source.md)   
 [Il recupero dei dati tramite AdomdDataReader](retrieving-data-using-the-adomddatareader.md)   
 [Recupero di dati tramite XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  
