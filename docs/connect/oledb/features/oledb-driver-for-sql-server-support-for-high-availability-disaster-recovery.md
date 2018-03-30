---
title: Driver OLE DB per SQL Server Support for High Availability, Disaster Recovery | Documenti Microsoft
description: Il Driver OLE DB per SQL Server il supporto per il ripristino di emergenza a disponibilità elevato
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9e2d236030dd77f2902e2e13575cc4aea2bc39ae
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>Driver OLE DB per SQL Server Support for High Availability, Disaster Recovery
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Questo argomento vengono illustrati i Driver OLE DB per il supporto di SQL Server (aggiunto [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Per altre informazioni su [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Listener del gruppo di disponibilità, connettività client e failover dell’applicazione &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md), [Creazione e configurazione di gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Clustering di failover e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) e [Repliche secondarie attive: Repliche secondarie leggibili &#40;Gruppi di disponibilità AlwaysOn&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 È possibile specificare il listener di un determinato gruppo di disponibilità nella stringa di connessione. Se un Driver OLE DB per SQL Server è connesso a un database in un gruppo di disponibilità che esegue il failover, la connessione originale viene interrotta e l'applicazione deve aprire una nuova connessione per continuare a funzionare dopo il failover.  
  
 Se non ci si connette a un listener del gruppo di disponibilità e se più indirizzi IP sono associati un nome host, il Driver OLE DB per SQL Server verranno scorsi in sequenza tutti gli indirizzi IP associati alla voce DNS. Questa operazione può richiedere tempi lunghi se il primo indirizzo IP restituito dal server DNS non è associato ad alcuna scheda di interfaccia di rete. Quando ci si connette a un listener del gruppo di disponibilità, il Driver OLE DB per SQL Server tenta di stabilire connessioni a tutti gli indirizzi IP in parallelo e se un tentativo di connessione ha esito positivo, il driver verrà rimosso qualsiasi tentativo di connessione in sospeso.  
  
> [!NOTE]  
>  L'aumento del timeout di connessione e l'implementazione della logica di riesecuzione per le connessioni aumentano le probabilità che un'applicazione si connetta a un gruppo di disponibilità. Inoltre, poiché potrebbe non essere possibile stabilire una connessione a causa del failover di un gruppo di disponibilità, è opportuno implementare la logica di riesecuzione delle connessioni, finché non si ottiene la riconnessione.  
  
## <a name="connecting-with-multisubnetfailover"></a>Connessione con MultiSubnetFailover  
 Specificare sempre **MultiSubnetFailover=Yes** in caso di connessione a un listener del gruppo di disponibilità di SQL Server 2012 o a un'istanza del cluster di failover di SQL Server 2012. **MultiSubnetFailover** consente di attivare un failover più veloce per tutti i gruppi di disponibilità e cluster di failover dell'istanza in SQL Server 2012, riducendo notevolmente il tempo di failover per singole e multi-subnet topologie AlwaysOn. Durante un failover su più subnet, verranno tentate connessioni in parallelo da parte del client. Durante un failover della subnet, il Driver OLE DB per SQL Server in modo aggressivo ritenterà la connessione TCP.  
  
 Il **MultiSubnetFailover** proprietà di connessione indica che l'applicazione viene distribuita in un gruppo di disponibilità o l'istanza del Cluster di Failover e il Driver OLE DB per SQL Server tenterà di connettersi al database di primario [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] indirizzi istanza prova a connettersi a tutti l'indirizzo IP. Quando si specifica **MultiSubnetFailover=Yes** per una connessione, i ripetuti tentativi di connessione TCP del client vengono eseguiti più rapidamente rispetto agli intervalli di ritrasmissione TCP predefiniti del sistema operativo. Ciò consente una riconnessione più veloce dopo il failover di un gruppo di disponibilità AlwaysOn o di un sempre nel Cluster di failover ed è applicabile a singolo e con più subnet gruppi di disponibilità sia istanze Cluster di Failover.  
  
 Per ulteriori informazioni sulle parole chiave delle stringhe di connessione, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 La specifica di **MultiSubnetFailover=Yes** durante la connessione a un oggetto diverso da un listener del gruppo di disponibilità o dall'istanza del cluster di failover non è supportata poiché potrebbe determinare un impatto negativo sulle prestazioni.  
  
 Utilizzare le linee guida seguenti per connettersi a un server in un gruppo di disponibilità o nell'istanza del cluster di failover:  
  
-   Usare la proprietà di connessione **MultiSubnetFailover** in caso di connessione a una singola subnet o a più subnet, in modo da migliorare le prestazioni.  
  
-   Per eseguire la connessione a un gruppo di disponibilità, specificare il listener del gruppo di disponibilità come server nella stringa di connessione.  
  
-   La connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configurata con più di 64 indirizzi IP determinerà un errore di connessione.  
  
-   Il comportamento di un'applicazione in cui viene usata la proprietà di connessione **MultiSubnetFailover** non è influenzato dal tipo di autenticazione, cioè dall'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], dall'autenticazione Kerberos, o dall’autenticazione di Windows.  
  
-   È possibile aumentare il valore di **loginTimeout** per adattarlo alla durata del failover e ridurre il numero di nuovi tentativi di connessione dell'applicazione.  
  
-   Le transazioni distribuite non sono supportate.  
  
 Se il routing di sola lettura non è attivo, non è possibile stabilire una connessione a un percorso di replica secondaria in un gruppo di disponibilità nelle situazioni seguenti:  
  
1.  Se il percorso di replica secondaria non è configurato per accettare le connessioni.  
  
2.  Se un'applicazione usa **ApplicationIntent=ReadWrite** (vedere di seguito) e il percorso di replica secondaria è configurato per l'accesso in sola lettura.  
  
 Una connessione non riesce se una replica primaria è configurata per rifiutare i carichi di lavoro in sola lettura e la stringa di connessione contiene **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aggiornamento per l'utilizzo di cluster su più subnet dal mirroring del database  
 Si verificherà un errore di connessione se nella stringa di connessione sono presenti le parole chiave di connessione **MultiSubnetFailover** e **Failover_Partner**. Si verificherà un errore anche se viene usato **MultiSubnetFailover** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restituisce una risposta del partner di failover in cui viene indicato che fa parte di una coppia del mirroring del database.  
  
 Se si aggiorna un Driver OLE DB per SQL Server che attualmente Usa il mirroring del database a uno scenario su più subnet, è necessario rimuovere il **Failover_Partner** proprietà di connessione e sostituirla con  **MultiSubnetFailover** impostato su **Sì** e sostituire il nome del server nella stringa di connessione con un listener del gruppo di disponibilità. Se in una stringa di connessione vengono usati **Failover_Partner** e **MultiSubnetFailover=Yes**, il driver genererà un errore. Se tuttavia in una stringa di connessione vengono usati **Failover_Partner** e **MultiSubnetFailover=No** (o **ApplicationIntent=ReadWrite**), l'applicazione userà il mirroring del database.  
  
 Il driver restituirà un errore se il mirroring del database viene usato nel database primario nel gruppo di disponibilità e se **MultiSubnetFailover=Yes** veine usato nella stringa di connessione a un database primario anziché a un listener del gruppo di disponibilità.  
  
## <a name="specifying-application-intent"></a>Specificazione della finalità dell'applicazione  
 Quando **ApplicationIntent = ReadOnly**, il client richiede un carico di lavoro di lettura durante la connessione a un database Always On abilitato. Tramite il server, la finalità verrà applicata al momento della connessione e durante un'istruzione di database USE, ma solo a un database abilitato per Always On.  
  
 La parola chiave **ApplicationIntent** non funziona con i database legacy di sola lettura.  
  
 Un database possibile consentire o negare carichi di lavoro di letture sul database di AlwaysOn destinazione. Questa operazione viene eseguita con la clausola **ALLOW_CONNECTIONS** delle istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] **PRIMARY_ROLE** e **SECONDARY_ROLE**.  
  
 La parola chiave **ApplicationIntent** è usata per abilitare il routing di sola lettura.  
  
## <a name="read-only-routing"></a>Routing di sola lettura  
 Il routing di sola lettura è una funzionalità che può garantire la disponibilità di una replica di sola lettura di un database. Per abilitare il routing di sola lettura:  
  
1.  È necessario connettersi a un listener del gruppo di disponibilità Always On.  
  
2.  La parola chiave della stringa di connessione **ApplicationIntent** deve essere impostata su **ReadOnly**.  
  
3.  Il gruppo di disponibilità deve essere configurato dall'amministratore del database per abilitare il routing di sola lettura.  
  
 È possibile che non tutte le connessioni in cui viene utilizzato il routing di sola lettura vengano stabilite alla stessa replica di sola lettura. Le modifiche nella sincronizzazione del database o nella configurazione di routing del server possono comportare connessioni client a repliche di sola lettura diverse. Per assicurare la connessione di tutte le richieste di sola lettura alla stessa replica di sola lettura, non passare un listener del gruppo di disponibilità alla parola chiave della stringa di connessione **Server**. Specificare invece il nome dell'istanza di sola lettura.  
  
 Il routing di sola lettura potrebbe impiegare più tempo a connettersi rispetto alla replica primaria poiché innanzitutto viene eseguita la connessione del routing di sola lettura alla replica primaria e, successivamente, viene cercata la replica secondaria migliore dal punto di vista della lettura. Per questo motivo è necessario aumentare il timeout di accesso.  

  
## <a name="ole-db"></a>OLE DB  
 Il Driver OLE DB per SQL Server supporta sia la **ApplicationIntent** e il **MultiSubnetFailover** parole chiave.   
  
 Le due parole chiave stringa di connessione OLE DB sono stati aggiunti per supportare [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nel Driver OLE DB per SQL Server:  
  
-   **ApplicationIntent** 
-   **MultiSubnetFailover**  
  
 Per ulteriori informazioni sulle parole chiave delle stringhe di connessione nel Driver OLE DB per SQL Server, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

### <a name="application-intent"></a>Finalità dell'applicazione 

 Le proprietà di connessione equivalenti sono:  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
 Un Driver OLE DB per un'applicazione OLE DB di SQL Server può utilizzare uno dei metodi per specificare la finalità dell'applicazione:  
  
 **IDBInitialize:: Initialize**  
 **IDBInitialize::Initialize** prevede l'uso del set di proprietà precedentemente configurato per inizializzare l'origine dati e creare l'oggetto origine dati. La finalità dell'applicazione viene specificata come proprietà del provider o come parte della stringa di proprietà estesa.  
  
 **IDataInitialize:: GetDatasource**  
 **IDataInitialize::GetDatasource** accetta una stringa di connessione di input che può contenere la parola chiave **Application Intent**.  
  
 **IDBProperties::GetProperties**  
 **IDBProperties::GetProperties** consente di recuperare il valore della proprietà attualmente impostata sull'origine dati.  È possibile recuperare il valore di **Application Intent** tramite la proprietà DBPROP_INIT_PROVIDERSTRING e la proprietà SSPROP_INIT_APPLICATIONINTENT.  
  
 **IDBProperties::SetProperties**  
 Per impostare il valore della proprietà **ApplicationIntent**, chiamare **IDBProperties::SetProperties** passando la proprietà **SSPROP_INIT_APPLICATIONINTENT** con un valore "**ReadWrite**" o "**ReadOnly**" o la proprietà **DBPROP_INIT_PROVIDERSTRING** con un valore contenente "**ApplicationIntent=ReadOnly**" o "**ApplicationIntent=ReadWrite**".  
  
 È possibile specificare la finalità dell'applicazione nel campo delle proprietà della finalità dell’applicazione della scheda Tutte nella finestra di dialogo **Proprietà di Data Link**.  
  
 Quando vengono stabilite connessioni implicite, per la connessione viene utilizzata l'impostazione relativa alla finalità dell'applicazione definita per la connessione padre. Analogamente, più sessioni create dalla stessa origine dati ereditano l'impostazione relativa alla finalità dell'applicazione definita per l'origine dati.  
  
### <a name="multisubnetfailover"></a>MultiSubnetFailover

La proprietà di connessione equivalente è:  
  
-   **SSPROP_INIT_MULTISUBNETFAILOVER**  

La proprietà SSPROP_INIT_MULTISUBNETFAILOVER è di tipo Boolean. La proprietà accetta valori di VARIANT_TRUE o VARIANT_FALSE.

Per impostare il valore della proprietà MultiSubnetFailover, chiamare **IDBProperties:: SetProperties** passando la proprietà SSPROP_INIT_MULTISUBNETFAILOVER con valore **VARIANT_TRUE** o **VARIANT_ FALSE**. 

#### <a name="example"></a>Esempio

```
DBPROP rgPropMultisubnet;

rgPropMultisubnet.dwPropertyID = SSPROP_INIT_MULTISUBNETFAILOVER;
rgPropMultisubnet.dwOptions = DBPROPOPTIONS_REQUIRED;
rgPropMultisubnet.dwStatus = DBPROPSTATUS_OK;
rgPropMultisubnet.colid = DB_NULLID;
V_VT(&(rgPropMultisubnet.vValue)) = VT_BOOL;
V_BOOL(&(rgPropMultisubnet.vValue)) = VARIANT_TRUE;

DBPROPSET PropSet;

PropSet.rgProperties = &rgPropMultisubnet;
PropSet.cProperties = 1;
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;
IDBProperties* pIDBProperties = NULL;
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);
pIDBProperties->SetProperties(1, &PropSet);
```



## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [Utilizzo di parole chiave delle stringhe di connessione con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)  
  
  
