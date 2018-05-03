---
title: Programmazione di Client ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ef37a558e3e8c0fb9b932cffe223508121b9103
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="adomdnet-client-programming"></a>Programmazione di client ADOMD.NET
  I componenti client ADOMD.NET si trovano all'interno di **Microsoft.AnalysisServices.AdomdClient** dello spazio dei nomi (in microsoft.analysisservices.adomdclient.dll). Questi componenti forniscono la funzionalità per client e applicazioni di livello intermedio per facilmente i dati di query e i metadati da un archivio dati analitici, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="using-the-adomdnet-client-objects"></a>Utilizzo di oggetti client ADOMD.NET  
 Nell'esecuzione di query su un'origine dati analitici è necessario eseguire un set di attività comuni. Nella tabella seguente vengono indicate le attività comuni in cui si utilizzano gli oggetti client ADOMD.NET per eseguire una query di questo tipo.  
  
|Attività|Description|  
|----------|-----------------|  
|[Per stabilire le connessioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)|Per stabilire connessioni con origini dati analitici, ad esempio database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], in ADOMD.NET viene utilizzato un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Per eseguire comandi, recuperare dati e recuperare metadati dall'origine dati analitici, è invece possibile utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
|[Recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)|Dopo che una connessione è stata stabilita, è possibile utilizzare un'ampia varietà di oggetti per recuperare informazioni sull'origine dati sottostante. Questa funzionalità consente alle applicazioni di adattarsi all'origine dati cui si sono connesse.|  
|[Esecuzione di comandi in un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)|L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> fornisce le interfacce necessarie per l'esecuzione di comandi sull'origine dati analitici sottostante.|  
|[Recupero di dati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)|Dopo l'esecuzione di un comando, i dati possono essere recuperati e analizzati tramite l'il <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, o **System.XmlReader** oggetti.|  
|[Esecuzione di transazioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-performing-transactions.md)|Tutte le azioni elencate nelle righe precedenti di questa tabella possono essere eseguite in una transazione di tipo Read Committed, in cui i blocchi condivisi vengono mantenuti durante la lettura dei dati per evitare letture dirty. I dati possono ancora essere modificati prima del termine della transazione, con la conseguente presenza di letture non ripetibili e di dati fantasma. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> fornisce le funzionalità per le transazioni in ADOMD.NET.|  
  
 L'interazione con la gerarchia di oggetti ADOMD.NET viene avviata in genere con uno o più oggetti del livello più alto della gerarchia, come descritto nella tabella seguente.  
  
|Per|Oggetto da utilizzare|  
|--------|---------------------|  
|Connessione a un'origine dati analitici|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> rappresenta una connessione sia a un'origine dati che ai metadati relativi. Ad esempio, è possibile connettersi a un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cubo locale (con estensione cub) file e quindi esaminare il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> proprietà per ottenere i metadati relativi ai cubi presenti nell'origine dati analitici. Questo oggetto rappresenta inoltre l'implementazione del **IDbConnection** interfaccia, un'interfaccia necessaria per tutti i provider di dati .NET Framework.|  
|Individuazione delle funzionalità di data mining dell'origine dati|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> espone numerose raccolte di data mining:<br /><br /><br /><br /> <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> che contiene un elenco di ogni modello di data mining nell'origine dati.<br /><br /><br /><br /> <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> che fornisce informazioni sugli algoritmi di data mining disponibili.<br /><br /><br /><br /> <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> che espone informazioni sulle strutture di data mining nel server.|  
|Esecuzione di query sull'origine dati|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> rappresenta l'istruzione o la query che verrà inviata al server. Una volta stabilita una connessione a un'origine dati, è possibile utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per eseguire istruzioni nel linguaggio supportato, ad esempio MDX (Multidimensional Expressions) o DMX (Data Mining Extensions). È inoltre possibile utilizzare un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per restituire risultati nel formato di oggetti <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.|  
|Recupero di dati in modo rapido ed efficiente|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> può essere creato mediante una chiamata al metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Questo oggetto implementa il **IDbDataReader** interfaccia dal **System. Data** dello spazio dei nomi della libreria di classi .NET Framework.|  
|Recupero di dati analitici con la quantità di metadati più elevata|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> può essere creato con una chiamata al metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Dopo che un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> ha restituito un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, è possibile esaminare i dati analitici contenuti da <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>.|  
|Recupero di metadati relativi a cubi, ad esempio dimensioni, misure, set denominati disponibili e così via|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> rappresenta metadati relativi a un cubo. È possibile fare riferimento all'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> da <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
|Recupero di dati tramite il **System.Data.IDbDataAdapter** interfaccia|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter> fornisce supporto di sola lettura per le applicazioni client .NET Framework esistenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di Server ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [Sviluppo con ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  
