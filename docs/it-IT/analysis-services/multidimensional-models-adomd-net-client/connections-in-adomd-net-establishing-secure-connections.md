---
title: Tentativo di stabilire connessioni protette in ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b92b5b1bfdec6e311b93743d22cc990623315a9a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connections-in-adomdnet---establishing-secure-connections"></a>Connessioni in ADOMD.NET - stabilire connessioni protette
  Quando si utilizza una connessione in ADOMD.NET, il metodo di sicurezza utilizzato per la connessione dipende dal valore del **ProtectionLevel** proprietà della stringa di connessione utilizzata quando si chiama il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> metodo il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Il **ProtectionLevel** proprietà offre quattro livelli di sicurezza: non autenticato, autenticato, firmato e crittografato. Nella tabella seguente vengono descritti i diversi livelli di sicurezza.  
  
> [!NOTE]  
>  Se si sceglie di utilizzare il pool di connessioni al database, quest'ultimo non sarà in grado di gestire la sicurezza poiché per il pool di connessioni al database è necessario che la stringa di connessione sia identica alle connessioni del pool. È pertanto necessario gestire la sicurezza in un altro punto.  
  
|Livello di sicurezza|Valore di ProtectionLevel|  
|--------------------|---------------------------|  
|*connessione non autenticata*<br /> Una connessione non autenticata non utilizza alcuna forma di autenticazione. Questo tipo di connessione rappresenta la forma di connessione maggiormente supportata, ma meno protetta.|**Nessuno**|  
|*connessione autenticata*<br /> Una connessione autenticata consente di autenticare l'utente che effettua la connessione, ma non protegge alcuna comunicazione aggiuntiva. Questo tipo di connessione risulta utile poiché consente di stabilire l'identità dell'utente o dell'applicazione che si connette a un'origine dati analitici.|**Connetti**|  
|*connessione firmata*<br /> Una connessione firmata consente di autenticare l'utente che richiede la connessione e garantisce inoltre che le trasmissioni non vengano modificate. Questo tipo di connessione risulta utile quando è necessario verificare l'autenticità dei dati trasferiti. Una connessione firmata impedisce tuttavia solo la modifica del contenuto del pacchetto di dati, ma non la relativa visualizzazione durante il transito.<br /><br /><br /><br /> Si noti che una connessione firmata è supportata solo per il codice XML per il provider di analisi forniti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|**Integrità PKT** o **PktIntegrity**|  
|*connessione crittografata*<br /> Una connessione crittografata rappresenta il tipo di connessione predefinito utilizzato da ADOMD.NET. Questo tipo di connessione consente di autenticare l'utente che richiede la connessione, nonché di crittografare i dati trasmessi. Una connessione crittografata rappresenta la forma di connessione più protetta che è possibile creare in ADOMD.NET. Il contenuto del pacchetto di dati non può essere né visualizzato né modificato con la conseguente protezione dei dati durante il transito.<br /><br /><br /><br /> Una connessione crittografata è supportata solo per il codice XML per il provider di analisi forniti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|**Privacy PKT** o **PktPrivacy**|  
  
 Non tutti i livelli di sicurezza sono tuttavia disponibili per tutti i tipi di connessioni:  
  
-   Una connessione TCP può utilizzare uno qualsiasi dei quattro livelli di sicurezza. Se utilizzata con la sicurezza integrata di Windows, una connessione TCP rappresenta infatti il metodo più protetto per connettersi a un'origine dati analitici.  
  
-   Una connessione HTTP può essere solo autenticata. Pertanto, il **ProtectionLevel** proprietà deve essere impostata su **Connetti**.  
  
-   Una connessione HTTPS può essere solo crittografata. Pertanto, il **ProtectionLevel** proprietà deve essere impostata su **Pkt Privacy** o **PktPrivacy**.  
  
## <a name="securing-tcp-connections"></a>Protezione di connessioni TCP  
 Per una connessione TCP, il **ProtectionLevel** proprietà supporta tutti i quattro livelli di sicurezza, come illustrato nella tabella seguente.  
  
|Valore di ProtectionLevel|Utilizzo con una connessione TCP|Risultati|  
|---------------------------|------------------------------|-------------|  
|**Nessuno**|Sì|Specifica di una connessione non autenticata.<br /><br /> Il provider richiede un flusso TCP, ma all'utente che effettua la richiesta del flusso non viene applicata alcuna forma di autenticazione.|  
|**Connetti**|Sì|Specifica di una connessione autenticata.<br /><br /> Un flusso TCP viene richiesto dal provider e successivamente il contesto di sicurezza dell'utente che richiede il flusso viene autenticato sul server: se l'autenticazione ha esito positivo, viene eseguita alcuna altra azione. Se l'autenticazione ha esito negativo, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> si disconnette dall'origine dati multidimensionale e viene generata un'eccezione.<br /><br /> Dopo l'esito positivo o negativo dell'autenticazione, il contesto di sicurezza utilizzato per autenticare la connessione viene eliminato.|  
|**Integrità PKT** o **PktIntegrity**|Sì|Specifica di una connessione firmata.<br /><br /> Il provider richiede un flusso TCP e successivamente il contesto di sicurezza relativo all'utente che effettua la richiesta del flusso viene autenticato nel server.<br /><br /> <br /><br /> Se l'autenticazione ha esito positivo, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> chiude il flusso TCP esistente e apre un flusso TCP firmato per gestire tutte le richieste. Ogni richiesta di dati o metadati viene autenticata tramite il contesto di sicurezza utilizzato per aprire la connessione. Ogni pacchetto viene inoltre firmato digitalmente per garantire che al payload del pacchetto TCP non sia stata apportata alcuna modifica.<br /><br /> <br /><br /> Se l'autenticazione ha esito negativo, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> si disconnette dall'origine dati multidimensionale e viene generata un'eccezione.|  
|**Privacy PKT** o **PktPrivacy**|Sì|Specifica di una connessione crittografata.<br /><br /> <br /><br /> Si noti che è anche possibile specificare una connessione crittografata non impostando la **ProtectionLevel** proprietà nella stringa di connessione.<br /><br /> <br /><br /> Il provider richiede un flusso TCP e successivamente il contesto di sicurezza relativo all'utente che effettua la richiesta del flusso viene autenticato nel server.<br /><br /> <br /><br /> Se l'autenticazione ha esito positivo, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> chiude il flusso TCP esistente e apre un flusso TCP crittografato per gestire tutte le richieste. Ogni richiesta di dati o metadati viene autenticata tramite il contesto di sicurezza utilizzato per aprire la connessione. Il payload di ogni pacchetto TCP viene inoltre crittografato tramite il metodo di crittografia di livello più elevato supportato sia dal provider che dall'origine dati multidimensionale.<br /><br /> <br /><br /> Se l'autenticazione ha esito negativo, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> si disconnette dall'origine dati multidimensionale e viene generata un'eccezione.|  
  
### <a name="using-windows-integrated-security-for-the-connection"></a>Utilizzo della sicurezza integrata di Windows per la connessione  
 La sicurezza integrata di Windows rappresenta il modo migliore di stabilire e di proteggere una connessione a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Nella sicurezza integrata di Windows le credenziali di sicurezza, ad esempio un nome utente o una password, non vengono rivelate durante il processo di autenticazione. Per stabilire l'identità, viene invece utilizzato l'ID di sicurezza del processo attualmente in esecuzione. Per la maggior parte delle applicazioni client, tale ID di sicurezza rappresenta l'identità dell'utente attualmente connesso.  
  
 Per utilizzare la sicurezza integrata di Windows, per la stringa di connessione è necessario specificare le impostazioni seguenti:  
  
-   Per il **la sicurezza integrata** proprietà, eseguire non impostare questa proprietà o impostare questa proprietà su **SSPI**.  
  
    > [!NOTE]  
    >  Sicurezza integrata di Windows è disponibile solo per le connessioni TCP poiché le connessioni HTTP devono utilizzare il **base** impostazione per il **la sicurezza integrata** proprietà.  
  
-   Per il **ProtectionLevel** proprietà, impostare questa proprietà su **Connetti**, **integrità Pkt**, o **Pkt Privacy**.  
  
## <a name="securing-http-connections"></a>Protezione di connessioni HTTP  
 Per proteggere esternamente comunicazioni HTTP con un'origine dati analitici, è possibile utilizzare HTTPS e SSL (Secure Sockets Layer).  
  
 Poiché un provider XMLA utilizza solo connessioni HTTP protette, una connessione HTTP in ADOMD.NET deve essere firmata, come illustrato nella tabella seguente.  
  
|Valore di ProtectionLevel|Utilizzo con HTTP o HTTPS|  
|---------------------------|----------------------------|  
|**Nessuno**|no|  
|**Connetti**|HTTP|  
|**Integrità PKT** o **PktIntegrity**|no|  
|**Privacy PKT** o **PktPrivacy**|HTTPS|  
  
### <a name="opening-a-secure-http-connection"></a>Apertura di una connessione HTTP protetta  
 Nell'esempio seguente viene illustrato come utilizzare ADOMD.NET per aprire una connessione HTTP per il **AdventureWorksAS** esempio [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database:  
  
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
 [Per stabilire le connessioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
  
