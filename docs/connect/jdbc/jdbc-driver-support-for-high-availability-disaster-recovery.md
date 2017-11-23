---
title: "Supporto del Driver JDBC per il ripristino di emergenza a disponibilità elevato | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
caps.latest.revision: "40"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 621f31fbeddee6ec3705396b5d049f5496f4ae04
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>Supporto di Microsoft JDBC Driver per il ripristino di emergenza a disponibilità elevata
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In questo argomento viene [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] il supporto per il ripristino di emergenza a disponibilità elevata [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]. Per altre informazioni su [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vedere la documentazione online di [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] .  
  
 A partire dalla versione 4.0 del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è possibile specificare il listener del gruppo di disponibilità di un (disponibilità elevata, ripristino di emergenza) del gruppo di disponibilità (AG) nella proprietà di connessione. Se un [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione è connessa a un database AlwaysOn che esegue il failover, la connessione originale viene interrotta e l'applicazione deve aprire una nuova connessione per continuare a funzionare dopo il failover. Nell'esempio [le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) sono state aggiunte in [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]:  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
Specificare multiSubnetFailover = true quando ci si connette al listener del gruppo di disponibilità di un gruppo di disponibilità o un'istanza del Cluster di Failover. Si noti che **multiSubnetFailover** è false per impostazione predefinita. Utilizzare **applicationIntent** per dichiarare il tipo di carico di lavoro dell'applicazione. Sezioni per ulteriori informazioni, vedere.
 
A partire dalla versione 6.0 di Microsoft JDBC Driver per SQL Server, una nuova proprietà di connessione **transparentNetworkIPResolution** (TNIR) viene aggiunto per la connessione trasparente ai gruppi di disponibilità Always On o su un server che ha più indirizzi IP associati. Quando **transparentNetworkIPResolution** è true, il driver tenta di connettersi al primo indirizzo IP disponibile. Se il primo tentativo non riesce, il driver tenta di connettersi a tutti gli indirizzi IP in parallelo fino a quando il timeout scade, ignorando eventuali tentativi di connessione in sospeso quando uno di essi ha esito positivo.   

Si noti che:
* transparentNetworkIPResolution è true per impostazione predefinita
* transparentNetworkIPResolution viene ignorato se multiSubnetFailover è true
* transparentNetworkIPResolution viene ignorata se viene utilizzato il mirroring del database
* transparentNetworkIPResolution viene ignorato se sono presenti più di 64 indirizzi IP
* Quando transparentNetworkIPResolution è true, il primo tentativo di connessione utilizza un valore di timeout di 500 ms. Resto dei tentativi di connessione seguono la stessa logica come la funzionalità multiSubnetFailover. 

> [!NOTE]  
Se si utilizza Microsoft JDBC Driver 4.2 (o inferiore) per SQL Server e **multiSubnetFailover** è false, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tenta di connettersi al primo indirizzo IP. Se il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non è possibile stabilire una connessione con il primo indirizzo IP, la connessione non riesce. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non tenterà di connettersi ad altri indirizzi IP successivi associati al server. 

  
> [!NOTE]  
>  L'aumento del timeout di connessione e l'implementazione della logica di riesecuzione per le connessioni aumentano le probabilità che un'applicazione si connetta a un gruppo di disponibilità. Inoltre, poiché potrebbe non essere possibile stabilire una connessione a causa del failover di un gruppo di disponibilità, è opportuno implementare la logica di riesecuzione delle connessioni, finché non si ottiene la riconnessione.  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>Connessione con MultiSubnetFailover  
 Specificare sempre **multiSubnetFailover = true** quando ci si connette al listener del gruppo di disponibilità di un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] gruppo di disponibilità o un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] istanza Cluster di Failover. **multiSubnetFailover** consente il failover più veloce per tutti i gruppi di disponibilità e le istanze del cluster di failover in [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] e riduce notevolmente il tempo di failover per le topologie AlwaysOn singole e su più subnet. Durante un failover su più subnet, verranno tentate connessioni in parallelo da parte del client. Durante un failover della subnet, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] riproverà continuamente la connessione TCP.  
  
 Il **multiSubnetFailover** proprietà di connessione indica che l'applicazione viene distribuita in un gruppo di disponibilità o l'istanza del Cluster di Failover e che il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tenterà di connettersi al database del server primario [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza tentando di connettersi a tutti gli IP indirizzi. Quando **MultiSubnetFailover = true** specificato per una connessione, il client riesegue i tentativi di connessione TCP più velocemente rispetto a intervalli di ritrasmissione TCP predefinita del sistema operativo. In tal modo si abilita la riconnessione a seguito di failover di un gruppo di disponibilità AlwaysOn o un'istanza del cluster di failover AlwaysOn ed è applicabile a istanze del cluster di failover o a gruppi di disponibilità su una singola subnet o su più subnet.  
  
 Per ulteriori informazioni sulle parole chiave di stringa di connessione nel [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Specifica di **multiSubnetFailover = true** quando la connessione a un elemento diverso da un listener del gruppo di disponibilità o l'istanza del Cluster di Failover può comportare un impatto negativo sulle prestazioni e non è supportata.  
  
 Se lo strumento di gestione della sicurezza non è installato, gli indirizzi IP virtuali vengono memorizzati nella cache di Java Virtual Machine per un periodo di tempo limitato definito, per impostazione predefinita, dall'implementazione JDK e dalle proprietà Java networkaddress.cache.ttl e networkaddress.cache.negative.ttl. Se lo strumento di gestione della sicurezza JDK è installato, gli indirizzi IP virtuali vengono memorizzati nella cache di Java Virtual Machine, ma la cache non viene aggiornata per impostazione predefinita. È consigliabile impostare "time-to-live" (networkaddress.cache.ttl) su un giorno per la cache di Java Virtual Machine. Se non si imposta il valore predefinito su un giorno (o un valore simile), il valore precedente non verrà eliminato dalla cache di Java Virtual Machine quando viene aggiunto o aggiornato un indirizzo IP virtuale. Per ulteriori informazioni su networkaddress.cache.ttl e networkaddress.cache.negative.ttl, vedere [http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Utilizzare le linee guida seguenti per connettersi a un server in un gruppo di disponibilità o nell'istanza del cluster di failover:  
  
-   Il driver genererà un errore se il **instanceName** proprietà di connessione viene utilizzata la stessa stringa di connessione come il **multiSubnetFailover** proprietà di connessione. Ciò riflette il fatto che SQL Browser non viene utilizzato in un gruppo di disponibilità. Tuttavia, se il **NumeroPorta** proprietà di connessione viene anche specificata, il driver ignorerà **instanceName** e utilizzare **NumeroPorta**.  
  
-   Utilizzare il **multiSubnetFailover** proprietà di connessione durante la connessione a una subnet singola o su più subnet, migliorerà le prestazioni.  
  
-   Per eseguire la connessione a un gruppo di disponibilità, specificare il listener del gruppo di disponibilità come server nella stringa di connessione. Ad esempio, jdbc:sqlserver://VNN1.  
  
-   La connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] configurata con più di 64 indirizzi IP determinerà un errore di connessione.  
  
-   Comportamento di un'applicazione che utilizza il **multiSubnetFailover** proprietà di connessione non è interessata in base al tipo di autenticazione: [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, l'autenticazione Kerberos o l'autenticazione di Windows.  
  
-   Aumentare il valore di **loginTimeout** per adattarlo alla durata del failover e ridurre i ripetuti tentativi di connessione dell'applicazione.  
  
-   Le transazioni distribuite non sono supportate.  
  
 Se il routing di sola lettura non è attivo, non è possibile stabilire una connessione a un percorso di replica secondaria in un gruppo di disponibilità nelle situazioni seguenti:  
  
1.  Se il percorso di replica secondaria non è configurato per accettare le connessioni.  
  
2.  Se un'applicazione utilizza **applicationIntent = ReadWrite** (come descritto di seguito) e il percorso di replica secondaria è configurato per l'accesso in sola lettura.  
  
 Una connessione non riesce se una replica primaria è configurata per rifiutare i carichi di lavoro in sola lettura e la stringa di connessione contiene **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aggiornamento per l'utilizzo di cluster su più subnet dal mirroring del database  
 Se si aggiorna un [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione che utilizza il mirroring del database a uno scenario su più subnet, è necessario rimuovere il **failoverPartner** proprietà di connessione e sostituirla con **multiSubnetFailover**  impostato su **true** e sostituire il nome del server nella stringa di connessione con un listener del gruppo di disponibilità. Se viene utilizzata una stringa di connessione **failoverPartner** e **multiSubnetFailover = true**, il driver genererà un errore. Tuttavia, se viene utilizzata una stringa di connessione **failoverPartner** e **multiSubnetFailover = false** (o **ApplicationIntent = ReadWrite**), l'applicazione utilizzerà database il mirroring.  
  
 Il driver restituirà un errore se il mirroring del database viene utilizzato nel database primario del gruppo di disponibilità e **multiSubnetFailover = true** viene utilizzata nella stringa di connessione che si connette a un database primario anziché a un gruppo di disponibilità listener.  
  
## <a name="specifying-application-intent"></a>Specificazione della finalità dell'applicazione  
 Quando **applicationIntent = ReadOnly**, il client richiede un carico di lavoro di sola lettura quando ci si connette a un database AlwaysOn abilitato. Le finalità verranno applicate dal server in fase di connessione e durante un istruzione di database USE, ma solo a un database abilitato per AlwaysOn.  
  
 Il **applicationIntent** (parola chiave) non funziona con i database legacy di sola lettura.  
  
 Un database può consentire o impedire carichi di lavoro di lettura nel database AlwaysOn di destinazione. Questa operazione viene eseguita con la clausola **ALLOW_CONNECTIONS** delle istruzioni [!INCLUDE[tsql](../../includes/tsql_md.md)] **PRIMARY_ROLE** e **SECONDARY_ROLE**.  
  
 Il **applicationIntent** parola chiave viene utilizzata per abilitare il routing di sola lettura.  
  
## <a name="read-only-routing"></a>Routing di sola lettura  
 Il routing di sola lettura è una funzionalità che può garantire la disponibilità di una replica di sola lettura di un database. Per abilitare il routing di sola lettura:  
  
1.  È necessario connettersi a un listener di un gruppo di disponibilità AlwaysOn.  
  
2.  Il **applicationIntent** parola chiave di stringa di connessione deve essere impostato su **ReadOnly**.  
  
3.  Il gruppo di disponibilità deve essere configurato dall'amministratore del database per abilitare il routing di sola lettura.  
  
 È possibile che non tutte le connessioni in cui viene utilizzato il routing di sola lettura vengano stabilite alla stessa replica di sola lettura. Le modifiche nella sincronizzazione del database o nella configurazione di routing del server possono comportare connessioni client a repliche di sola lettura diverse. Per garantire che tutte le richieste di sola lettura di connettersi alla stessa replica di sola lettura, non passare un listener del gruppo di disponibilità o l'indirizzo IP virtuale per il **serverName** parola chiave di stringa di connessione. Specificare invece il nome dell'istanza di sola lettura.  
  
 Per il routing di sola lettura può essere necessario più tempo rispetto alla connessione alla replica primaria, in quanto viene innanzitutto eseguita la connessione alla replica primaria e quindi viene individuata la miglior replica secondaria leggibile disponibile. Per questo motivo è necessario aumentare il timeout di accesso.  
  
## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Nuovi metodi che supportano multiSubnetFailover e applicationIntent  
 I metodi seguenti forniscono accesso a livello di codice per il **multiSubnetFailover**, **applicationIntent** e **transparentNetworkIPResolution** stringa di connessione parole chiave:  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [Sqlserverdriver](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 Il **getMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** e **setTransparentNetworkIPResolution** vengono inoltre aggiunti i metodi [classe SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [ Classe SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), e [classe SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
## <a name="ssl-certificate-validation"></a>Convalida del certificato SSL  
 Un gruppo di disponibilità è costituito da più server fisici. [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]aggiunto il supporto per **nome soggetto alternativo** in certificati SSL in modo più host possano essere associati con lo stesso certificato. Per ulteriori informazioni su SSL, vedere [supporto SSL comprensione](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il Driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [Impostazione delle proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md)  
  
  
