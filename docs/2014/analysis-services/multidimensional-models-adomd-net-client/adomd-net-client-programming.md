---
title: Programmazione di Client ADOMD.NET | Documenti Microsoft
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
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 55156115-ecd1-4ed9-876e-23406af9bbf9
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9faa64cce77c883ed6adb86bca6d50f32f015c97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168408"
---
# <a name="adomdnet-client-programming"></a>Programmazione di client ADOMD.NET
  I componenti client ADOMD.NET si trovano nello spazio dei nomi `Microsoft.AnalysisServices.AdomdClient` (in microsoft.analysisservices.adomdclient.dll). Questi componenti forniscono la funzionalità per client e le applicazioni di livello intermedio a facilmente eseguire query sui dati e metadati da un archivio dati analitici, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="using-the-adomdnet-client-objects"></a>Utilizzo di oggetti client ADOMD.NET  
 Nell'esecuzione di query su un'origine dati analitici è necessario eseguire un set di attività comuni. Nella tabella seguente vengono indicate le attività comuni in cui si utilizzano gli oggetti client ADOMD.NET per eseguire una query di questo tipo.  
  
|Attività|Description|  
|----------|-----------------|  
|[Implementazione di connessioni in ADOMD.NET](connections-in-adomd-net.md)|Per stabilire connessioni con origini dati analitici, ad esempio database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], in ADOMD.NET viene utilizzato un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Per eseguire comandi, recuperare dati e recuperare metadati dall'origine dati analitici, è invece possibile utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
|[Recupero di metadati da un'origine dati analitici](retrieving-metadata-from-an-analytical-data-source.md)|Dopo che una connessione è stata stabilita, è possibile utilizzare un'ampia varietà di oggetti per recuperare informazioni sull'origine dati sottostante. Questa funzionalità consente alle applicazioni di adattarsi all'origine dati cui si sono connesse.|  
|[Esecuzione di comandi in un'origine dati analitici](executing-commands-against-an-analytical-data-source.md)|L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> fornisce le interfacce necessarie per l'esecuzione di comandi sull'origine dati analitici sottostante.|  
|[Recupero di dati da un'origine dati analitici](retrieving-data-from-an-analytical-data-source.md)|Dopo l'esecuzione di un comando, i dati possono essere recuperati e analizzati tramite l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> o `System.XmlReader`.|  
|[Esecuzione di transazioni in ADOMD.NET](../../relational-databases/native-client-ole-db-transactions/transactions.md)|Tutte le azioni elencate nelle righe precedenti di questa tabella possono essere eseguite in una transazione di tipo Read Committed, in cui i blocchi condivisi vengono mantenuti durante la lettura dei dati per evitare letture dirty. I dati possono ancora essere modificati prima del termine della transazione, con la conseguente presenza di letture non ripetibili e di dati fantasma. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> fornisce le funzionalità per le transazioni in ADOMD.NET.|  
  
 L'interazione con la gerarchia di oggetti ADOMD.NET viene avviata in genere con uno o più oggetti del livello più alto della gerarchia, come descritto nella tabella seguente.  
  
|Per|Oggetto da utilizzare|  
|--------|---------------------|  
|Connessione a un'origine dati analitici|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> rappresenta una connessione sia a un'origine dati che ai metadati relativi. Ad esempio, è possibile connettersi a un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cubo locale (con estensione cub) file e quindi esaminare il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> proprietà per ottenere i metadati relativi ai cubi presenti nell'origine dati analitici. Tale oggetto rappresenta inoltre l'implementazione dell'interfaccia `IDbConnection`, necessaria per tutti i provider di dati .NET Framework.|  
|Individuazione delle funzionalità di data mining dell'origine dati|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> espone numerose raccolte di data mining:<br /><br /> -La <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> contiene un elenco di ogni modello di data mining nell'origine dati.<br />-La <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> fornisce informazioni sugli algoritmi di data mining disponibili.<br />-La <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> espone informazioni sulle strutture di data mining nel server.|  
|Esecuzione di query sull'origine dati|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> rappresenta l'istruzione o la query che verrà inviata al server. Una volta stabilita una connessione a un'origine dati, è possibile utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per eseguire istruzioni nel linguaggio supportato, ad esempio MDX (Multidimensional Expressions) o DMX (Data Mining Extensions). È inoltre possibile utilizzare un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per restituire risultati nel formato di oggetti <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.|  
|Recupero di dati in modo rapido ed efficiente|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> può essere creato mediante una chiamata al metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Tale oggetto implementa l'interfaccia `IDbDataReader` dello spazio dei nomi `System.Data` della libreria di classi .NET Framework.|  
|Recupero di dati analitici con la quantità di metadati più elevata|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> può essere creato con una chiamata al metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>. Dopo che un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> ha restituito un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, è possibile esaminare i dati analitici contenuti da <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>.|  
|Recupero di metadati relativi a cubi, ad esempio dimensioni, misure, set denominati disponibili e così via|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> rappresenta metadati relativi a un cubo. È possibile fare riferimento all'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> da <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
|Recupero di dati tramite l'interfaccia `System.Data.IDbDataAdapter`|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter> fornisce supporto di sola lettura per le applicazioni client .NET Framework esistenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di Server ADOMD.NET](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [Sviluppo con ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  