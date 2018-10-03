---
title: Per stabilire le connessioni in ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a338d1902440fe6489b7c4c91176899999aa25fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172021"
---
# <a name="establishing-connections-in-adomdnet"></a>Implementazione di connessioni in ADOMD.NET
  In ADOMD.NET è usare il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto per aprire connessioni con origini dati analitici, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] i database. Quando la connessione non è più necessaria, deve essere chiusa in modo esplicito.  
  
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
 Dopo avere specificato la stringa di connessione, è necessario utilizzare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> per aprire la connessione. Quando si apre un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, è possibile impostare i diversi livelli di sicurezza per la connessione. Il livello di sicurezza utilizzato per la connessione dipende dal valore dell'impostazione `ProtectionLevel` della stringa di connessione. Per altre informazioni sull'apertura di connessioni protette in ADOMD.NET, vedere [tentativo di stabilire connessioni protette in ADOMD.NET](connections-in-adomd-net-establishing-secure-connections.md).  
  
## <a name="working-with-a-connection"></a>Utilizzo di una connessione  
 Ogni connessione aperta esiste in una sessione, in cui viene fornito il supporto per le operazioni con stato. Una sessione può essere condivisa da più di una connessione aperta. La condivisione di una sessione consente a più di un client di utilizzare lo stesso contesto. Per altre informazioni, vedere [uso di connessioni e sessioni in ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
 È possibile utilizzare una connessione aperta per recuperare metadati e dati e per eseguire comandi. Per altre informazioni, vedere [recupero di metadati da un'origine dati analitici](retrieving-metadata-from-an-analytical-data-source.md), [recupero dei dati da un'origine dati analitici](retrieving-data-from-an-analytical-data-source.md), e [l'esecuzione di comandi su un dati analitici Origine](executing-commands-against-an-analytical-data-source.md).  
  
 Quando la connessione è aperta, è possibile recuperare dati e metadati ed eseguire comandi da una transazione di tipo Read Committed, in cui i blocchi condivisi vengono mantenuti durante la lettura dei dati per evitare letture dirty. I dati possono ancora essere modificati prima del termine della transazione, con la conseguente presenza di letture non ripetibili e di dati fantasma. Per altre informazioni, vedere [esecuzione di transazioni in ADOMD.NET](../../relational-databases/native-client-ole-db-transactions/transactions.md).  
  
## <a name="closing-a-connection"></a>Chiusura di una connessione  
 È consigliabile chiudere in modo esplicito un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> non appena la connessione non è più necessaria. Per chiudere in modo esplicito la connessione, utilizzare i metodi `Close` e `Dispose` dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Una connessione che non viene chiusa in modo esplicito, ma cui è consentito uscire dall'ambito, potrebbe non rilasciare le risorse del server in modo sufficientemente rapido per consentire alle applicazioni client di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con elevato grado di concorrenza di aprire nuove connessioni in modo efficiente. In base al modo in cui è stata creata la connessione, la sessione utilizzata dall'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> può rimanere attiva se la connessione non viene chiusa in modo esplicito.  
  
 Per altre informazioni sulle sessioni, vedere [uso di connessioni e sessioni in ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
> [!IMPORTANT]  
>  Nel metodo `Finalize` di ogni classe implementata, non chiamare i metodi `Close` o `Dispose` di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> o di qualsiasi altro oggetto gestito. In un finalizzatore rilasciare solo le risorse non gestite di proprietà diretta della classe implementata. Se la classe implementata non è proprietaria di alcuna risorsa non gestita, non includere un metodo `Finalize` nella relativa definizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](adomd-net-client-programming.md)  
  
  
