---
title: Utilizzo con il modello a oggetti ADOMD.NET | Documenti Microsoft
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
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de2d73db65d10acdea5ec0c221eb994700ba5f41
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156096"
---
# <a name="working-with-the-adomdnet-object-model"></a>Utilizzo del modello a oggetti ADOMD.NET
  In ADOMD.NET è disponibile un modello a oggetti per la visualizzazione dei cubi e degli oggetti subordinati contenuti in un'origine dati analitica. Tramite il modello a oggetti tuttavia non è possibile utilizzare tutti i metadati per un'origine dati analitici specifica, ma è possibile accedere solo alle informazioni più utili da visualizzare in un'applicazione client in modo da consentire all'utente di creare comandi in modo interattivo. A causa della complessità ridotta dei metadati da presentare, il modello a oggetti ADOMD.NET risulta più facile da utilizzare.  
  
 Nel modello a oggetti ADOMD.NET l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> consente di accedere alle informazioni sui cubi OLAP (Online Analytical Processing), sui modelli di data mining definiti in un'origine dati analitici e sugli oggetti correlati, ad esempio dimensioni, set denominati e algoritmi di data mining.  
  
## <a name="retrieving-olap-metadata"></a>Recupero di metadati OLAP  
 Ogni oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> dispone di una raccolta di oggetti <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> che rappresentano i cubi disponibili per l'utente o per l'applicazione. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> espone informazioni sul cubo e sui diversi oggetti correlati al cubo, ad esempio dimensioni, indicatori di prestazioni chiave, misure, set denominati e così via.  
  
 Se possibile, è necessario utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> per rappresentare metadati nelle applicazioni client progettate per supportare più server OLAP o per visualizzare e accedere a metadati generali.  
  
> [!NOTE]  
>  Per metadati specifici del provider o per visualizzare e accedere a metadati dettagliati, utilizzare set di righe dello schema per il recupero dei metadati stessi. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](retrieving-metadata-working-with-schema-rowsets.md)).  
  
 Nell'esempio seguente viene utilizzato l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> per recuperare i cubi visibili e le relative dimensioni dal server locale:  
  
 [!code-csharp[Adomd.NetClient#RetrieveCubesAndDimensions](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#retrievecubesanddimensions)]  
  
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
 [Recupero di metadati da un'origine dati analitici](retrieving-metadata-from-an-analytical-data-source.md)  
  
  