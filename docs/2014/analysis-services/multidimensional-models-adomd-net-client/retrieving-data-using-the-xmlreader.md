---
title: Recupero di dati tramite XmlReader | Microsoft Docs
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
- retrieving data
- XmlReader object
- data retrieval [ADOMD.NET], XmlReader object
ms.assetid: 420ec40e-be2d-413a-b4b2-6d2b1756e270
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa47902131522f807ebe96b0b14a3df28aaf657f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267567"
---
# <a name="retrieving-data-using-the-xmlreader"></a>Recupero di dati tramite XmlReader
  La classe `XmlReader`, appartenente allo spazio dei nomi `System.Xml` per la libreria di classi Microsoft .NET Framework, è analoga alla classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> poiché anche la classe `XmlReader` consente di accedere rapidamente ai dati, in modalità non in cache e forward-only. Se non è necessaria una vista analitica dei dati in memoria tramite l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, l'oggetto `XmlReader` rappresenta la soluzione ideale per il recupero di dati XML, soprattutto nel caso in cui siano presenti grandi quantità di dati. Poiché `XmlReader` trasmette flussi di dati, `XmlReader` non deve recuperare e memorizzare nella cache tutti i dati prima di esporli al chiamante, situazione che si verificherebbe invece nel caso in cui un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> venisse utilizzato per convertire la risposta XMLA in una rappresentazione analitica del modello a oggetti.  
  
 La classe `XmlReader` consente di accedere direttamente alla risposta XMLA ricevuta da ADOMD.NET quando viene chiamato il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Poiché i dati recuperati sono rappresentati da codice XML non elaborato, è necessario analizzare manualmente i dati e i metadati. Non appena i dati sono stati recuperati, l'oggetto `XmlReader` deve essere chiuso.  
  
## <a name="retrieving-data-and-metadata"></a>Recupero di dati e metadati  
 Per utilizzare la classe `XmlReader` per recuperare i dati, effettuare le seguenti operazioni:  
  
1.  **Creare una nuova istanza dell'oggetto.**  
  
     Per creare una nuova istanza della classe `XmlReader`, chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Recuperare i dati.**  
  
     Dopo che il comando ha eseguito la query e ha restituito una classe `XmlReader`, è necessario analizzare i dati e i metadati. I dati e i metadati XML vengono presentati nel formato nativo utilizzato dal provider di XML for Analysis. Per la maggior parte dei provider di XML for Analysis, il formato nativo è costituito dal formato `MDDataSet`. Il formato `MDDataSet` fornisce sia i dati che i metadati per i set di celle in una struttura corretta. Per ulteriori informazioni sul formato `MDDataSet`, vedere la specifica XML for Analysis.  
  
3.  **Chiudere il lettore.**  
  
     È sempre necessario chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> al termine dell'utilizzo dell'oggetto `XmlReader`. Mentre un oggetto `XmlReader` è aperto, tale oggetto `XmlReader`  detiene l'utilizzo esclusivo dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> utilizzato per eseguire il comando. Non sarà pertanto possibile eseguire alcun comando che utilizza tale oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, ad esempio la creazione di un altro oggetto `XmlReader` o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, fino a quando non si chiude l'oggetto `XmlReader` originale.  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>Esempio di recupero di dati tramite XmlReader  
 Nell'esempio seguente viene creato un comando e vengono recuperati i dati come classe `XmlReader` e il contenuto del file viene restituito alla console.  
  
 [!code-csharp[Adomd.NetClient#OutputDataWithXML](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#outputdatawithxml)]  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di dati da un'origine dati analitici](retrieving-data-from-an-analytical-data-source.md)   
 [Il recupero dei dati tramite l'oggetto CellSet](retrieving-data-using-the-cellset.md)   
 [Recupero di dati tramite AdomdDataReader](retrieving-data-using-the-adomddatareader.md)  
  
  
