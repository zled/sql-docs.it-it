---
title: Recupero di dati da un'origine dati analitici | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cfc0c783e8c61689d8f5b0ca3bab6ded39a57a4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212381"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Recupero di dati da un'origine dati analitici
  Dopo avere creato una connessione e creato la query, è possibile recuperare qualsiasi dato. In ADOMD.NET è possibile recuperare i dati utilizzando tre oggetti diversi, ovvero <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> e <xref:System.Xml.XmlReader> tramite una chiamata a uno dei metodi `Execute` dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
 Per ognuno di questi tre l'interattività e l'overhead sono bilanciati:  
  
-   *Interattività* si intende la semplicità d'uso e quantità di informazioni disponibili nel modello a oggetti.  
  
-   *Overhead* si riferisce alla quantità di traffico che un modello a oggetti genera nella connessione di rete al server, la quantità di memoria necessaria per il modello a oggetti e la velocità con cui il modello a oggetti recupera i dati.  
  
 Per selezionare l'oggetto per il recupero di dati che soddisfa meglio le esigenze dell'applicazione, nella tabella seguente vengono evidenziate le differenze tra interattività e overhead per ogni oggetto.  
  
|Object|Interattività|Overhead|Mantenimento della dimensionalità|Informazioni di utilizzo|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Massima|Moderatamente elevato, con un conseguente recupero più lento dei dati|Sì|[Recupero di dati tramite l'oggetto CellSet](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Moderata|Moderata|no|[Popolamento di un set di dati da un oggetto DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Moderata|Moderata|no|[Recupero di dati tramite AdomdDataReader](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Minima|Minimo, con un conseguente recupero più rapido dei dati|Sì|[Recupero di dati tramite XmlReader](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](adomd-net-client-programming.md)  
  
  
