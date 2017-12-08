---
title: Utilizzo con il modello a oggetti ADOMD.NET | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fac5e4a825c4b30e7b9f102d03c5793438e2a2d7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="retrieving-metadata---working-with-adomdnet-object-model"></a>Il recupero dei metadati - utilizzo di modello a oggetti ADOMD.NET
  In ADOMD.NET è disponibile un modello a oggetti per la visualizzazione dei cubi e degli oggetti subordinati contenuti in un'origine dati analitica. Tramite il modello a oggetti tuttavia non è possibile utilizzare tutti i metadati per un'origine dati analitici specifica, ma è possibile accedere solo alle informazioni più utili da visualizzare in un'applicazione client in modo da consentire all'utente di creare comandi in modo interattivo. A causa della complessità ridotta dei metadati da presentare, il modello a oggetti ADOMD.NET risulta più facile da utilizzare.  
  
 Nel modello a oggetti ADOMD.NET l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> consente di accedere alle informazioni sui cubi OLAP (Online Analytical Processing), sui modelli di data mining definiti in un'origine dati analitici e sugli oggetti correlati, ad esempio dimensioni, set denominati e algoritmi di data mining.  
  
## <a name="retrieving-olap-metadata"></a>Recupero di metadati OLAP  
 Ogni oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> dispone di una raccolta di oggetti <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> che rappresentano i cubi disponibili per l'utente o per l'applicazione. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> espone informazioni sul cubo e sui diversi oggetti correlati al cubo, ad esempio dimensioni, indicatori di prestazioni chiave, misure, set denominati e così via.  
  
 Se possibile, è necessario utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> per rappresentare metadati nelle applicazioni client progettate per supportare più server OLAP o per visualizzare e accedere a metadati generali.  
  
> [!NOTE]  
>  Per metadati specifici del provider o per visualizzare e accedere a metadati dettagliati, utilizzare set di righe dello schema per il recupero dei metadati stessi. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nell'esempio seguente viene utilizzato l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> per recuperare i cubi visibili e le relative dimensioni dal server locale:  
  
 [!code-cs[Adomd.NetClient#RetrieveCubesAndDimensions](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-metadata-work_1_1.cs)]  
  
## <a name="retrieving-data-mining-metadata"></a>Recupero di metadati di data mining  
 Ogni oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> dispone di diversi raccolte che forniscono informazioni sulle funzionalità di data mining dell'origine dati:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> che contiene un elenco di ogni modello di data mining nell'origine dati.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> che fornisce informazioni sugli algoritmi di data mining disponibili.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> che espone informazioni sulle strutture di data mining nel server.  
  
 Per stabilire le modalità di esecuzione di query su un modello di data mining nel server, eseguire un'iterazione nella raccolta <xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A>. Ogni oggetto <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn> espone le caratteristiche seguenti:  
  
-   Indicazione dell'oggetto come colonna di input o meno (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>).  
  
-   Indicazione dell'oggetto come colonna di stima o meno (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>).  
  
-   Valori associati a una colonna discreta (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>).  
  
-   Tipo di dati nella colonna (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>).  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
