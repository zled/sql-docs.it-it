---
title: Recupero di dati tramite XmlReader | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c8f4392b3cd37abb57ef2b7294e4b1ed223b27a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="retrieving-data-using-the-xmlreader"></a>Recupero di dati tramite XmlReader
  Il **XmlReader** parte della classe di **System. XML** spazio dei nomi per la libreria di classi Microsoft .NET Framework, è simile al <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> classe in cui il **XmlReader**classe fornisce anche veloce, non in cache e forward-only ai dati. Se non è necessario per la visualizzazione in memoria, analisi dei dati mediante il <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> oggetto, il **XmlReader** oggetto è perfetto per il recupero dei dati XML, in particolare per grandi quantità di dati. Poiché **XmlReader** flussi di dati, **XmlReader** non è necessario recuperare e memorizzare nella cache di tutti i dati prima di esporli al chiamante, come nel caso un <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> oggetti utilizzati per convertire il Risposta XML for Analysis in una rappresentazione del modello oggetto analitici.  
  
 Il **XmlReader** classe fornisce accesso diretto al codice XML per la risposta XMLA ricevuta da ADOMD.NET quando il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> metodo il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> viene chiamato l'oggetto. Poiché i dati recuperati sono rappresentati da codice XML non elaborato, è necessario analizzare manualmente i dati e i metadati. Non appena i dati sono stati recuperati, il **XmlReader** oggetto deve essere chiuso.  
  
## <a name="retrieving-data-and-metadata"></a>Recupero di dati e metadati  
 Utilizzare il **XmlReader** classe per recuperare i dati, questi passaggi:  
  
1.  **Creare una nuova istanza dell'oggetto.**  
  
     Per creare una nuova istanza del **XmlReader** (classe), chiamare il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> metodo il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> oggetto.  
  
2.  **Recuperare i dati.**  
  
     Dopo il comando esegue la query e restituisce un **XmlReader**, è necessario analizzare i dati e metadati. I dati e i metadati XML vengono presentati nel formato nativo utilizzato dal provider di XML for Analysis. Per la maggior parte delle XML per i provider di analisi, il formato nativo è la **MDDataSet** formato. Il **MDDataSet** formato fornisce dati e metadati per un set di celle in un formato ben strutturato. Per ulteriori informazioni sul **MDDataSet** di formato, vedere la specifica XML for Analysis.  
  
3.  **Chiudere il lettore.**  
  
     È necessario chiamare sempre il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> metodo al termine dell'utilizzo di **XmlReader** oggetto. Mentre un **XmlReader** è aperto, tale **XmlReader** ha l'uso esclusivo del <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto utilizzato per eseguire il comando. Non sarà in grado di eseguire qualsiasi comando che utilizza tale <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, inclusa la creazione di un altro **XmlReader** o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, finché non si chiude originale **XmlReader**.  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>Esempio di recupero di dati tramite XmlReader  
 Nell'esempio seguente esegue un comando e recupera i dati come un **XmlReader**, l'output di contenuto del file nella console.  
  
 [!code-cs[Adomd.NetClient#OutputDataWithXML](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-data-using-th_1_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di dati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)   
 [Recupero di dati tramite il set di celle](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)   
 [Recupero di dati tramite AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)  
  
  
