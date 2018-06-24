---
title: Recupero di dati da un'origine dati analitici | Documenti Microsoft
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
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6e6243a815b399c91a2cd7aaa9eca712c6c569bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054399"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Recupero di dati da un'origine dati analitici
  Dopo avere creato una connessione e creato la query, è possibile recuperare qualsiasi dato. In ADOMD.NET è possibile recuperare i dati utilizzando tre oggetti diversi, ovvero <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> e <xref:System.Xml.XmlReader> tramite una chiamata a uno dei metodi `Execute` dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
 Per ognuno di questi tre l'interattività e l'overhead sono bilanciati:  
  
-   *Interattività* si intende la semplicità d'uso e la quantità di informazioni disponibili tramite il modello a oggetti.  
  
-   *Overhead* si intende la quantità di traffico che un modello a oggetti genera nella connessione di rete al server, la quantità di memoria necessaria per il modello a oggetti e la velocità con cui il modello a oggetti recupera i dati.  
  
 Per selezionare l'oggetto per il recupero di dati che soddisfa meglio le esigenze dell'applicazione, nella tabella seguente vengono evidenziate le differenze tra interattività e overhead per ogni oggetto.  
  
|Object|Interattività|Overhead|Mantenimento della dimensionalità|Informazioni di utilizzo|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Massima|Moderatamente elevato, con un conseguente recupero più lento dei dati|Sì|[Recupero di dati tramite l'oggetto CellSet](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Moderata|Moderata|no|[Popolamento di un set di dati da un oggetto DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Moderata|Moderata|no|[Recupero di dati tramite AdomdDataReader](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Minima|Minimo, con un conseguente recupero più rapido dei dati|Sì|[Recupero di dati tramite XmlReader](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](adomd-net-client-programming.md)  
  
  