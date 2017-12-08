---
title: Per stabilire le connessioni in ADOMD.NET | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 262b81a3177806ead76bbff15f770e0d1d0418aa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="connections-in-adomdnet"></a>Connessioni in ADOMD.NET
  In ADOMD.NET, utilizzare il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto per aprire connessioni con origini dati analitici, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database. Quando la connessione non è più necessaria, deve essere chiusa in modo esplicito.  
  
## <a name="opening-a-connection"></a>Apertura di una connessione  
 Per aprire una connessione in ADOMD.NET, è necessario prima specificare una stringa di connessione a un'origine dati analitici valida e un database. Successivamente è necessario stabilire in modo esplicito la connessione con tale origine dati.  
  
### <a name="specifying-a-multidimensional-data-source"></a>Specifica di un'origine dati multidimensionale  
 Per specificare un'origine dati analitici e un database, impostare la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. La stringa di connessione specificata per la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> è una stringa conforme a OLE DB. ADOMD.NET utilizza la stringa di connessione specificata per determinare il modo in cui connettersi al server.  
  
 La proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> può essere impostata su un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> esistente o durante la creazione di un'istanza di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Nel codice seguente viene illustrato come impostare la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> quando si crea una connessione ADOMD:  
  
```vb  
Dim advwrksConnection As New AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS")  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString)  
```  
  
```csharp  
AdomdConnection advwrksConnection = new AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS");  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString);  
```  
  
### <a name="opening-a-connection-to-the-data-source"></a>Stabilire una connessione con l'origine dati  
 Dopo avere specificato la stringa di connessione, è necessario utilizzare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> per aprire la connessione. Quando si apre un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, è possibile impostare i diversi livelli di sicurezza per la connessione. Il livello di sicurezza utilizzato per la connessione dipende dal valore del **ProtectionLevel** impostazione della stringa di connessione. Per ulteriori informazioni sull'apertura di connessioni protette in ADOMD.NET, vedere [tentativo di stabilire connessioni protette in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-establishing-secure-connections.md).  
  
## <a name="working-with-a-connection"></a>Utilizzo di una connessione  
 Ogni connessione aperta esiste in una sessione, in cui viene fornito il supporto per le operazioni con stato. Una sessione può essere condivisa da più di una connessione aperta. La condivisione di una sessione consente a più di un client di utilizzare lo stesso contesto. Per ulteriori informazioni, vedere [utilizzo di connessioni e sessioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
 È possibile utilizzare una connessione aperta per recuperare metadati e dati e per eseguire comandi. Per ulteriori informazioni, vedere [recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md), [recupero dei dati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md), e [l'esecuzione di comandi su un dati analitici Origine](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md).  
  
 Quando la connessione è aperta, è possibile recuperare dati e metadati ed eseguire comandi da una transazione di tipo Read Committed, in cui i blocchi condivisi vengono mantenuti durante la lettura dei dati per evitare letture dirty. I dati possono ancora essere modificati prima del termine della transazione, con la conseguente presenza di letture non ripetibili e di dati fantasma. Per ulteriori informazioni, vedere [esecuzione di transazioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-performing-transactions.md).  
  
## <a name="closing-a-connection"></a>Chiusura di una connessione  
 È consigliabile chiudere in modo esplicito un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> non appena la connessione non è più necessaria. Per chiudere in modo esplicito la connessione, utilizzare il **chiudere** e **Dispose** metodi il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto.  
  
 Una connessione che non viene chiusa in modo esplicito, ma cui è consentito uscire dall'ambito, potrebbe non rilasciare le risorse del server in modo sufficientemente rapido per consentire alle applicazioni client di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con elevato grado di concorrenza di aprire nuove connessioni in modo efficiente. In base al modo in cui è stata creata la connessione, la sessione utilizzata dall'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> può rimanere attiva se la connessione non viene chiusa in modo esplicito.  
  
 Per ulteriori informazioni sulle sessioni, vedere [utilizzo di connessioni e sessioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
> [!IMPORTANT]  
>  Nel **Finalize** metodo di qualsiasi classe implementata, non chiamare il **Chiudi** o **Dispose** metodi di un <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> oggetto, o qualsiasi altro oggetto gestito. In un finalizzatore rilasciare solo le risorse non gestite di proprietà diretta della classe implementata. Se la classe implementata non è il proprietario delle risorse non gestite, non includere un **Finalize** metodo nella definizione della classe.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
