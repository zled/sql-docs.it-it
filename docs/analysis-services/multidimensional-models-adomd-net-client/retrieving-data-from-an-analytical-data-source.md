---
title: Recupero di dati da un'origine dati analitici | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e2dbd10be43b0d0e64b4068e6f93c0bba2457d4e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Moderata|Moderata|No|[Popolamento di un set di dati da un oggetto DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Moderata|Moderata|No|[Recupero di dati tramite AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Minima|Minimo, con un conseguente recupero più rapido dei dati|Sì|[Recupero di dati tramite XmlReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
