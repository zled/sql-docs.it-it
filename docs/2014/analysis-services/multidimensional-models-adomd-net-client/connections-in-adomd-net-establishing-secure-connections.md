---
title: Tentativo di stabilire connessioni protette in ADOMD.NET | Microsoft Docs
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
- connections [ADOMD.NET]
- security [ADOMD.NET]
ms.assetid: b084d447-1456-45a4-8e0e-746c07d7d6fd
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d97079ca400d92502cf3ff217137eb6f32d1920d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180858"
---
# <a name="establishing-secure-connections-in-adomdnet"></a>Implementazione di connessioni protette in ADOMD.NET
  Quando si implementa una connessione in ADOMD.NET, il metodo di sicurezza utilizzato per la connessione dipende dal valore della proprietà `ProtectionLevel` della stringa di connessione utilizzata quando si chiama il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> di <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Alla proprietà `ProtectionLevel` sono associati quattro livelli di sicurezza, ovvero non autenticato, autenticato, firmato e crittografato. Nella tabella seguente vengono descritti i diversi livelli di sicurezza.  
  
> [!NOTE]  
>  Se si sceglie di utilizzare il pool di connessioni al database, quest'ultimo non sarà in grado di gestire la sicurezza poiché per il pool di connessioni al database è necessario che la stringa di connessione sia identica alle connessioni del pool. È pertanto necessario gestire la sicurezza in un altro punto.  
  
|Livello di sicurezza|Valore di ProtectionLevel|  
|--------------------|---------------------------|  
|*connessione non autenticata*<br /> Una connessione non autenticata non utilizza alcuna forma di autenticazione. Questo tipo di connessione rappresenta la forma di connessione maggiormente supportata, ma meno protetta.|`None`|  
|*connessione autenticata*<br /> Una connessione autenticata consente di autenticare l'utente che effettua la connessione, ma non protegge alcuna comunicazione aggiuntiva. Questo tipo di connessione risulta utile poiché consente di stabilire l'identità dell'utente o dell'applicazione che si connette a un'origine dati analitici.|`Connect`|  
|*connessione firmata*<br /> Una connessione firmata consente di autenticare l'utente che richiede la connessione e garantisce inoltre che le trasmissioni non vengano modificate. Questo tipo di connessione risulta utile quando è necessario verificare l'autenticità dei dati trasferiti. Una connessione firmata impedisce tuttavia solo la modifica del contenuto del pacchetto di dati, ma non la relativa visualizzazione durante il transito. **Nota:** una connessione firmata è supportata solo per il provider di XML for Analysis fornito da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|`Pkt Integrity` o `PktIntegrity`|  
|*connessione crittografata*<br /> Una connessione crittografata rappresenta il tipo di connessione predefinito utilizzato da ADOMD.NET. Questo tipo di connessione consente di autenticare l'utente che richiede la connessione, nonché di crittografare i dati trasmessi. Una connessione crittografata rappresenta la forma di connessione più protetta che è possibile creare in ADOMD.NET. Il contenuto del pacchetto di dati non può essere né visualizzato né modificato con la conseguente protezione dei dati durante il transito. **Nota:** una connessione crittografata è supportata solo per il provider di XML for Analysis fornito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|`Pkt Privacy` o `PktPrivacy`|  
  
 Non tutti i livelli di sicurezza sono tuttavia disponibili per tutti i tipi di connessioni:  
  
-   Una connessione TCP può utilizzare uno qualsiasi dei quattro livelli di sicurezza. Se utilizzata con la sicurezza integrata di Windows, una connessione TCP rappresenta infatti il metodo più protetto per connettersi a un'origine dati analitici.  
  
-   Una connessione HTTP può essere solo autenticata. La proprietà `ProtectionLevel` deve essere impostata pertanto su `Connect`.  
  
-   Una connessione HTTPS può essere solo crittografata. La proprietà `ProtectionLevel` deve essere impostata pertanto su `Pkt Privacy` o su `PktPrivacy`.  
  
## <a name="securing-tcp-connections"></a>Protezione di connessioni TCP  
 Per una connessione TCP, la proprietà `ProtectionLevel` supporta tutti i quattro livelli di sicurezza, come illustrato nella tabella seguente.  
  
|Valore di ProtectionLevel|Utilizzo con una connessione TCP|Risultati|  
|---------------------------|------------------------------|-------------|  
|`None`|Sì|Specifica di una connessione non autenticata.<br /><br /> Il provider richiede un flusso TCP, ma all'utente che effettua la richiesta del flusso non viene applicata alcuna forma di autenticazione.|  
|`Connect`|Sì|Specifica di una connessione autenticata.<br /><br /> Il provider richiede un flusso TCP e successivamente il contesto di sicurezza relativo all'utente che effettua la richiesta del flusso viene autenticato nel server.<br /><br /> -Se l'autenticazione riesce, non viene eseguita alcuna altra azione.<br />-Se l'autenticazione non riesce, il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto di disconnette dall'origine dati multidimensionale e viene generata un'eccezione.<br /><br /> Dopo l'esito positivo o negativo dell'autenticazione, il contesto di sicurezza utilizzato per autenticare la connessione viene eliminato.|  
|`Pkt Integrity` o `PktIntegrity`|Sì|Specifica di una connessione firmata.<br /><br /> Il provider richiede un flusso TCP e successivamente il contesto di sicurezza relativo all'utente che effettua la richiesta del flusso viene autenticato nel server.<br /><br /> -Se l'autenticazione riesce, il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto chiude il flusso TCP esistente e apre un flusso TCP firmato per gestire tutte le richieste. Ogni richiesta di dati o metadati viene autenticata tramite il contesto di sicurezza utilizzato per aprire la connessione. Ogni pacchetto viene inoltre firmato digitalmente per garantire che al payload del pacchetto TCP non sia stata apportata alcuna modifica.<br />-Se l'autenticazione non riesce, il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto di disconnette dall'origine dati multidimensionale e viene generata un'eccezione.|  
|`Pkt Privacy` o `PktPrivacy`|Sì|Specifica di una connessione crittografata. **Nota:** è inoltre possibile specificare una connessione crittografata non impostando la `ProtectionLevel` proprietà nella stringa di connessione. <br /><br /> Il provider richiede un flusso TCP e successivamente il contesto di sicurezza relativo all'utente che effettua la richiesta del flusso viene autenticato nel server.<br /><br /> -Se l'autenticazione riesce, il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto chiude il flusso TCP esistente e si apre un flusso TCP crittografato per gestire tutte le richieste. Ogni richiesta di dati o metadati viene autenticata tramite il contesto di sicurezza utilizzato per aprire la connessione. Il payload di ogni pacchetto TCP viene inoltre crittografato tramite il metodo di crittografia di livello più elevato supportato sia dal provider che dall'origine dati multidimensionale.<br />-Se l'autenticazione non riesce, il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto di disconnette dall'origine dati multidimensionale e viene generata un'eccezione.|  
  
### <a name="using-windows-integrated-security-for-the-connection"></a>Utilizzo della sicurezza integrata di Windows per la connessione  
 La sicurezza integrata di Windows rappresenta il modo migliore di stabilire e di proteggere una connessione a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Nella sicurezza integrata di Windows le credenziali di sicurezza, ad esempio un nome utente o una password, non vengono rivelate durante il processo di autenticazione. Per stabilire l'identità, viene invece utilizzato l'ID di sicurezza del processo attualmente in esecuzione. Per la maggior parte delle applicazioni client, tale ID di sicurezza rappresenta l'identità dell'utente attualmente connesso.  
  
 Per utilizzare la sicurezza integrata di Windows, per la stringa di connessione è necessario specificare le impostazioni seguenti:  
  
-   La proprietà `Integrated Security` non deve essere impostata su alcun valore o deve essere impostata su `SSPI`.  
  
    > [!NOTE]  
    >  La sicurezza integrata di Windows è disponibile solo per le connessioni TCP poiché le connessioni HTTP devono utilizzare l'impostazione `Basic` per la proprietà `Integrated Security`.  
  
-   La proprietà `ProtectionLevel` deve essere impostata su `Connect`, `Pkt Integrity` o su `Pkt Privacy`.  
  
## <a name="securing-http-connections"></a>Protezione di connessioni HTTP  
 Per proteggere esternamente comunicazioni HTTP con un'origine dati analitici, è possibile utilizzare HTTPS e SSL (Secure Sockets Layer).  
  
 Poiché un provider XMLA utilizza solo connessioni HTTP protette, una connessione HTTP in ADOMD.NET deve essere firmata, come illustrato nella tabella seguente.  
  
|Valore di ProtectionLevel|Utilizzo con HTTP o HTTPS|  
|---------------------------|----------------------------|  
|`None`|no|  
|`Connect`|HTTP|  
|`Pkt Integrity` o `PktIntegrity`|no|  
|`Pkt Privacy` o `PktPrivacy`|HTTPS|  
  
### <a name="opening-a-secure-http-connection"></a>Apertura di una connessione HTTP protetta  
 Nell'esempio seguente viene illustrato come utilizzare ADOMD.NET per aprire una connessione HTTP per il database di esempio `AdventureWorksAS` di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:  
  
```vb  
Public Function GetAWEncryptedConnection( _  
    Optional ByVal serverName As String = "https:\\localhost\isapy\msmdpump.dll") _  
    As AdomdConnection  
  
    Dim strConnectionString As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' To establish an encrypted connection, set the   
        ' ProtectionLevel setting to PktPrivacy.  
        strConnectionString = "DataSource=" & serverName & ";" & _  
            "Catalog=AdventureWorksAS;" & _  
            "ProtectionLevel=PktPrivacy;"  
  
        ' Note that username and password are not supplied here.  
        ' The current security context is used for authentication  
        ' purposes.  
  
        objConnection.ConnectionString = strConnectionString  
        objConnection.Open()  
    Catch ex As Exception  
        objConnection = Nothing  
        Throw ex  
    Finally  
        ' Return the encrypted connection.  
        GetAWEncryptedConnection = objConnection  
    End Try  
End Function  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di connessioni in ADOMD.NET](connections-in-adomd-net.md)  
  
  
