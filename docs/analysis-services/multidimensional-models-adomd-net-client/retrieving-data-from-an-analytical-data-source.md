---
title: Recupero di dati da un'origine dati analitici | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 36d17c0e902b5853f6b2d550c34ba96a94e02886
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Recupero di dati da un'origine dati analitici
  Dopo avere creato una connessione e creato la query, è possibile recuperare qualsiasi dato. In ADOMD.NET, è possibile recuperare i dati utilizzando tre oggetti diversi (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, e <xref:System.Xml.XmlReader>) chiamando uno del **Execute** metodi di <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> oggetto.  
  
 Per ognuno di questi tre l'interattività e l'overhead sono bilanciati:  
  
-   *Interattività* si intende la facilità di utilizzo e la quantità di informazioni disponibili tramite il modello a oggetti.  
  
-   *Overhead* si intende la quantità di traffico che genera un modello a oggetti tramite la connessione di rete al server, la quantità di memoria necessaria per il modello a oggetti e la velocità con cui il modello a oggetti recupera i dati.  
  
 Per selezionare l'oggetto per il recupero di dati che soddisfa meglio le esigenze dell'applicazione, nella tabella seguente vengono evidenziate le differenze tra interattività e overhead per ogni oggetto.  
  
|Oggetto|Interattività|Overhead|Mantenimento della dimensionalità|Informazioni di utilizzo|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Massima|Moderatamente elevato, con un conseguente recupero più lento dei dati|Sì|[Recupero di dati tramite l'oggetto CellSet](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Moderata|Moderata|no|[Popolamento di un set di dati da un oggetto DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Moderata|Moderata|no|[Recupero di dati tramite AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Minima|Minimo, con un conseguente recupero più rapido dei dati|Sì|[Recupero di dati tramite XmlReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
