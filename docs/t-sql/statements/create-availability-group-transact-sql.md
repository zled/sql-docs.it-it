---
title: "CREARE il gruppo di disponibilità (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AVAILABILITY GROUP
- CREATE_AVAILABILITY_TSQL
- CREATE_AVAILABILITY_GROUP_TSQL
- CREATE AVAILABILITY GROUP
- CREATE AVAILABILITY
- AVAILABILITY_GROUP_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- CREATE AVAILABILITY GROUP statement
- Availability Groups [SQL Server], creating
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: a3d55df7-b4e4-43f3-a14b-056cba36ab98
caps.latest.revision: "196"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 35ccffcfbdce2c10b20c8459e59a1c2d41962088
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-availability-group-transact-sql"></a>CREATE AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo gruppo di disponibilità, se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è abilitata per la funzionalità [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
> [!IMPORTANT]  
>  Eseguire CREATE AVAILABILITY GROUP nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che si desidera utilizzare come replica primaria iniziale del nuovo gruppo di disponibilità. Questa istanza del server deve trovarsi in un nodo WSFC (Windows Server Failover Clustering).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```SQL  
  
CREATE AVAILABILITY GROUP group_name  
   WITH (<with_option_spec> [ ,...n ] )  
   FOR [ DATABASE database_name [ ,...n ] ]  
   REPLICA ON <add_replica_spec> [ ,...n ]  
   AVAILABILITY GROUP ON <add_availability_group_spec> [ ,...2 ]  
   [ LISTENER ‘dns_name’ ( <listener_option> ) ]  
[ ; ]  
  
<with_option_spec>::=   
    AUTOMATED_BACKUP_PREFERENCE = { PRIMARY | SECONDARY_ONLY| SECONDARY | NONE }  
  | FAILURE_CONDITION_LEVEL  = { 1 | 2 | 3 | 4 | 5 }   
  | HEALTH_CHECK_TIMEOUT = milliseconds  
  | DB_FAILOVER  = { ON | OFF }   
  | DTC_SUPPORT  = { PER_DB | NONE }  
  | BASIC  
  | DISTRIBUTED
  | REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = { integer }
  | CLUSTER_TYPE = { WSFC | EXTERNAL | NONE } 
  
<add_replica_spec>::=  
  <server_instance> WITH  
    (  
       ENDPOINT_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT | CONFIGURATION_ONLY },  
       FAILOVER_MODE = { AUTOMATIC | MANUAL | EXTERNAL }  
       [ , <add_replica_option> [ ,...n ] ]  
    )   
  
  <add_replica_option>::=  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
            [ ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL } ]   
        [,] [ READ_ONLY_ROUTING_URL = 'TCP://system-address:port' ]  
     } )  
     | PRIMARY_ROLE ( {   
            [ ALLOW_CONNECTIONS = { READ_WRITE | ALL } ]   
        [,] [ READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE } ]  
     } )  
     | SESSION_TIMEOUT = integer  
  
<add_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = MANUAL,  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<listener_option> ::=  
   {  
      WITH DHCP [ ON ( <network_subnet_option> ) ]  
    | WITH IP ( { ( <ip_address_option> ) } [ , ...n ] ) [ , PORT = listener_port ]  
   }  
  
  <network_subnet_option> ::=  
     ‘four_part_ipv4_address’, ‘four_part_ipv4_mask’    
  
  <ip_address_option> ::=  
     {   
        ‘four_part_ipv4_address’, ‘four_part_ipv4_mask’  
      | ‘ipv6_address’  
     }  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome_gruppo*  
 Specifica il nome del nuovo gruppo di disponibilità. *nome_gruppo* deve essere un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [identificatore](../../relational-databases/databases/database-identifiers.md), e deve essere univoco in tutti i gruppi di disponibilità nel cluster WSFC. La lunghezza massima consentita per il nome del gruppo di disponibilità è 128 caratteri.  
  
 AUTOMATED_BACKUP_PREFERENCE  **=**  {PRIMARIO | SECONDARY_ONLY | SECONDARIO | NONE}  
 Specifica le preferenze per la modalità di valutazione della replica primaria da parte di un processo di backup nella scelta della posizione in cui eseguire i backup. È possibile generare uno script affinché un processo di backup specifico prenda in considerazione le preferenze di backup automatico. È importante comprendere che le preferenze non vengono applicate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pertanto non incidono sui backup ad hoc.  
  
 I valori supportati sono i seguenti:  
  
 PRIMARY  
 Specifica che i backup devono essere sempre eseguiti sulla replica primaria. Questa opzione è utile se sono necessarie funzionalità di backup, ad esempio la creazione di backup differenziali, che non sono supportate quando il backup viene eseguito su una replica secondaria.  
  
> [!IMPORTANT]  
>  Se si intende usare il log shipping per preparare un qualsiasi database secondario per un gruppo di disponibilità, impostare la preferenza di backup automatico su **Primario** finché tutti i database secondari non saranno stati preparati e uniti in join al gruppo di disponibilità.  
  
 SECONDARY_ONLY  
 Specifica che i backup non devono mai essere eseguiti sulla replica primaria. Se la replica primaria è l'unica replica online, il backup non viene eseguito.  
  
 SECONDARY  
 Specifica che i backup devono essere eseguiti su una replica secondaria tranne quando la replica primaria è l'unica replica online. In tal caso il backup deve essere eseguito sulla replica primaria. Questo è il comportamento predefinito.  
  
 Nessuno  
 Specifica che si preferisce che i processi di backup ignorino il ruolo delle repliche di disponibilità nella scelta della replica per l'esecuzione dei backup. Si noti che i processi di backup potrebbero valutare altri fattori, ad esempio la priorità di backup di ogni replica di disponibilità in combinazione con lo stato operativo e lo stato connesso.  
  
> [!IMPORTANT]  
>  Non è prevista l'applicazione dell'impostazione AUTOMATED_BACKUP_PREFERENCE. L'interpretazione di questa preferenza dipende dall'eventuale logica su cui si basano gli script dei processi di backup per i database in un determinato gruppo di disponibilità. L'impostazione relativa alle preferenze di backup automatico non incide sui backup ad hoc. Per ulteriori informazioni, vedere [configurare il Backup su repliche di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
> [!NOTE]  
>  Per visualizzare la preferenza di backup automatico di un gruppo di disponibilità esistente, selezionare il **automated_backup_preference** o **automated_backup_preference_desc** colonna il [ availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) vista del catalogo. Inoltre, [Sys. fn_hadr_backup_is_preferred_replica &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md) può essere usato per determinare la replica di backup preferita.  Questa funzione restituisce 1 per almeno una delle repliche, anche quando `AUTOMATED_BACKUP_PREFERENCE = NONE`.  
  
 FAILURE_CONDITION_LEVEL  **=**  {1 | 2 | **3** | 4 | 5}  
 Specifica quale condizione di errore attivano un failover automatico per questo gruppo di disponibilità. FAILURE_CONDITION_LEVEL viene impostato a livello di gruppo ma è rilevante solo sulle repliche di disponibilità sono configurate per la modalità di disponibilità con commit sincrono (AVAILIBILITY_MODE  **=**  SYNCHRONOUS_COMMIT). Inoltre, le condizioni di errore possono attivare un failover automatico solo se entrambe le repliche primarie e secondarie sono configurate per la modalità di failover automatico (FAILOVER_MODE  **=**  automatico) e la replica secondaria è attualmente sincronizzata con la replica primaria.  
  
 I livelli delle condizioni di errore (1-5) vanno dal livello 1, meno restrittivo, al livello 5, più restrittivo. Un livello di condizione specifico include tutti i livelli meno restrittivi. Il livello della condizione più restrittivo, ovvero il livello 5, include pertanto i quattro livelli della condizione meno restrittivi (1-4), il livello 4 include i livelli 1-3 e così via. Nella tabella seguente viene descritta la condizione di errore che corrisponde a ciascun livello.  
  
|Level|Condizione di errore|  
|-----------|-----------------------|  
|1|Specifica che deve essere avviato un failover automatico quando si verifica una delle condizioni seguenti:<br /><br /> -La [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio è inattivo.<br /><br /> -Il lease del gruppo di disponibilità per la connessione al cluster WSFC scade poiché non viene ricevuto alcun Acknowledgement dall'istanza del server. Per altre informazioni, vedere [Funzionamento: timeout lease di SQL Server Always On](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-AlwaysOn-lease-timeout.aspx).|  
|2|Specifica che deve essere avviato un failover automatico quando si verifica una delle condizioni seguenti:<br /><br /> -L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non si connette al cluster, e viene superata la soglia HEALTH_CHECK_TIMEOUT specificata dall'utente del gruppo di disponibilità.<br /><br /> -La replica di disponibilità è in stato di errore.|  
|3|Specifica che deve essere avviato un failover automatico in caso di errori interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] critici, ad esempio spinlock orfani, gravi violazioni dell'accesso in scrittura o dumping eccessivo.<br /><br /> Questo è il comportamento predefinito.|  
|4|Specifica che deve essere avviato un failover automatico in caso di errori interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con gravità moderata, ad esempio una condizione persistente di memoria insufficiente nel pool di risorse interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|5|Specifica che deve essere avviato un failover automatico in caso di qualsiasi condizione di errore qualificata, tra cui:<br /><br /> -Esaurimento dei thread di lavoro del motore SQL.<br /><br /> -Il rilevamento di un deadlock irrisolvibile.|  
  
> [!NOTE]  
>  L'assenza di risposta da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle richieste del client non è rilevante per i gruppi di disponibilità.  
  
 I valori FAILURE_CONDITION_LEVEL e HEALTH_CHECK_TIMEOUT, definire un *criteri di failover flessibili* per un gruppo specifico. fornendo un controllo granulare sulle condizioni che devono causare un failover automatico. Per ulteriori informazioni, vedere [criteri di Failover flessibili per Failover automatico di un gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/flexible-automatic-failover-policy-availability-group.md).  
  
 HEALTH_CHECK_TIMEOUT  **=**  *millisecondi*  
 Specifica il tempo di attesa (in millisecondi) per il [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) sistema stored procedure per restituire informazioni sull'integrità del server prima che il cluster WSFC presupponga che l'istanza del server sia lenta o bloccata. HEALTH_CHECK_TIMEOUT viene impostato a livello di gruppo ma è rilevante solo sulle repliche di disponibilità che sono configurate per la modalità di disponibilità con commit sincrono con failover automatico (AVAILIBILITY_MODE  **=**  SINCRONO _COMMIT).  Inoltre, un timeout controllo integrità può attivare un failover automatico solo se entrambe le repliche primarie e secondarie sono configurate per la modalità di failover automatico (FAILOVER_MODE  **=**  automatico) e il database secondario replica è attualmente sincronizzata con la replica primaria.  
  
 Il valore predefinito di HEALTH_CHECK_TIMEOUT è 30000 millisecondi (30 secondi). Il valore minimo è 15000 millisecondi (15 secondi) e il valore massimo è 4294967295 millisecondi.  
  
> [!IMPORTANT]  
>  **sp_server_diagnostics** non esegue controlli di integrità a livello di database.  
  
 DB_FAILOVER  **=**  {ON | OFF}  
 Specifica la risposta da intraprendere quando un database nella replica primaria è offline. Quando è impostata su ON, qualsiasi stato diverso da in linea per un database nel gruppo di disponibilità viene attivato un failover automatico. Quando questa opzione è impostata su OFF, solo l'integrità dell'istanza viene utilizzato per attivare il failover automatico.  
  
  Per ulteriori informazioni su questa impostazione, vedere [opzione di rilevamento dello stato di livello Database](../../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md) 
  
 DTC_SUPPORT  **=**  {PER_DB | NONE}  
 Specifica se le transazioni tra database sono supportate tramite il distributed transaction coordinator (DTC). Le transazioni tra database sono supportate solo a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. PER_DB crea il gruppo di disponibilità con il supporto per queste transazioni. Per altre informazioni, vedere [Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
 BASIC  
 Utilizzato per creare un gruppo di disponibilità di base. Gruppi di disponibilità di base sono limitati a un database e due repliche: una replica primaria e una replica secondaria. Questa opzione è una sostituzione per la funzionalità in SQL Server Standard Edition di mirroring di database deprecata. Per ulteriori informazioni, vedere [base i gruppi di disponibilità &#40; Sempre in gruppi di disponibilità &#41; ](../../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md). I gruppi di disponibilità di base sono supportati a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  

 DISTRIBUTED  
 Utilizzato per creare un gruppo di disponibilità distribuito. Questa opzione viene utilizzata con il parametro AVAILABILITY GROUP ON per la connessione di due gruppi di disponibilità nel cluster Windows Server Failover.  Per altre informazioni, vedere [Gruppi di disponibilità distribuiti &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md). Gruppi di disponibilità distribuiti sono supportati a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. 

 REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT   
 Introdotti in SQL Server 2017. Utilizzato per impostare un numero minimo di repliche secondarie sincrone necessarie per eseguire il commit prima che il database primario viene eseguito il commit di una transazione. Garantisce che rimane in attesa delle transazioni di SQL Server fino a quando non vengono aggiornati i log delle transazioni per il numero minimo delle repliche secondarie. Il valore predefinito è 0, che fornisce lo stesso comportamento di SQL Server 2016. Il valore minimo è 0. Il valore massimo è il numero di repliche meno 1. Questa opzione mette in relazione alle repliche in modalità con commit sincrono. Durante le repliche sono in modalità con commit sincrono, scritture nella replica primaria attendere scritture sulle repliche secondarie sincrone vengano eseguito il commit nel log delle transazioni del database di replica. Se un Server SQL che ospita una replica sincrona secondaria si blocca, SQL Server che ospita la replica primaria contrassegna tale replica secondaria come non SINCRONIZZATA e continuare. Quando il database non rispondono torna online è in uno stato "not synced" e la replica è contrassegnata come non integro fino a quando il database primario può rendere sincroni nuovamente. Questa impostazione garantisce che la replica primaria attende che il numero minimo di repliche è eseguito il commit di ogni transazione. Se il numero minimo delle repliche non è disponibile quindi eseguire il commit nel database primario. Per il tipo di cluster `EXTERNAL` l'impostazione viene modificata quando il gruppo di disponibilità viene aggiunta a una risorsa cluster. Vedere [elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](../../linux/sql-server-linux-availability-group-ha.md).

 CLUSTER_TYPE  
 Introdotti in SQL Server 2017. Utilizzato per identificare se il gruppo di disponibilità è in un Windows Server Failover Cluster (WSFC).  Quando il gruppo di disponibilità si trova su un'istanza del cluster di failover in un cluster di failover di Windows Server, impostare su WSFC. Impostato su esterno quando il cluster è gestito da Gestione cluster di cui non è un cluster di failover di Windows Server, ad esempio Linux Pacemaker. Impostata su NONE se non si utilizza WSFC per il coordinamento di cluster del gruppo di disponibilità. Ad esempio, quando un gruppo di disponibilità include i server Linux con alcun gestore cluster. 

 DATABASE *database_name*  
 Specifica un elenco di uno o più database utente nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale, cioè l'istanza del server in cui si desidera creare il gruppo di disponibilità. È possibile specificare più database per un gruppo di disponibilità, ma ogni database può appartenere a un solo gruppo di disponibilità. Per informazioni sul tipo di database che può supportare un gruppo di disponibilità, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md). Per scoprire quali database locali già appartenenti a un gruppo di disponibilità, vedere il **replica_id** colonna il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
 La clausola DATABASE è facoltativa. Se viene omesso, il nuovo gruppo di disponibilità è vuoto.  
  
 Dopo aver creato il gruppo di disponibilità, connettersi a ogni istanza del server che ospita una replica secondaria e preparare ogni database secondario e aggiungerlo al gruppo di disponibilità. Per altre informazioni, vedere [Avviare lo spostamento dati su un database secondario Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
> [!NOTE]  
>  Successivamente sarà possibile aggiungere a un gruppo di disponibilità database idonei nell'istanza del server in cui è ospitata la replica primaria corrente. È inoltre possibile rimuovere un database da un gruppo di disponibilità. Per altre informazioni, vedere [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
 REPLICA ON  
 Specifica da una a cinque istanze di SQL Server per ospitare le repliche di disponibilità nel nuovo gruppo di disponibilità.  Ogni replica viene specificata dall'indirizzo della relativa istanza del server seguito da una clausola WITH (…). Come minimo, è necessario specificare l'istanza del server locale, che diventa la replica primaria iniziale. È eventualmente possibile specificare anche un massimo di quattro repliche secondarie.  
  
 È necessario creare un join di ogni replica secondaria al gruppo di disponibilità. Per altre informazioni, vedere [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
> [!NOTE]  
>  Se si specifica di meno di quattro repliche secondarie, quando si crea un gruppo di disponibilità, è possibile un'altra replica secondaria in qualsiasi momento utilizzando il [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione. È anche possibile usare questa istruzione per rimuovere qualsiasi replica secondaria da un gruppo di disponibilità esistente.  
  
 \<istanza_server > specifica l'indirizzo dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è l'host per una replica. Il formato dell'indirizzo dipende dal fatto che l'istanza sia l'istanza predefinita o un'istanza denominata e se si tratti di un'istanza autonoma o un'istanza del cluster di failover (FCI), come segue:  
  
 { '*_sistema*[\\*nome_istanza*]' | '*nome_rete_FCI*[\\*nome_istanza*]' }  
  
 I componenti di questo indirizzo sono i seguenti:  
  
 *_sistema*  
 Nome NetBIOS del computer in cui si trova l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il computer deve essere un nodo WSFC.  
  
 *nome_rete_FCI*  
 Nome di rete usato per accedere a un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Usare questo nome se l'istanza del server partecipa come partner di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'esecuzione di SELECT [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) in un'istanza FCI istanza del server restituisce l'intera '*nome_rete_fci*[\\*instance_name*]' stringa (che è la nome completo della replica).  
  
 *nome_istanza*  
 È il nome di un'istanza di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è ospitato da *nome_sistema* o *nome_rete_fci* e HADR con il servizio è abilitato. Per un'istanza del server predefinita, *nome_istanza* è facoltativo. Per il nome dell'istanza non viene fatta distinzione tra maiuscole e minuscole. In un'istanza del server autonomo, il nome del valore è uguale al valore restituito dall'esecuzione di SELECT [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md).  
  
 \  
 Separatore usato solo quando si specifica *instance_name*, per separarlo da *nome_sistema* o *nome_rete_fci*.  
  
 Per informazioni sui prerequisiti per i nodi WSFC e le istanze del server, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 ENDPOINT_URL **='**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica il percorso URL per il [endpoint del mirroring del database](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita la replica di disponibilità che si sta definendo nella clausola REPLICA ON corrente.  
  
 La clausola ENDPOINT_URL è obbligatoria. Per altre informazioni, vedere [Specificare l'URL dell'endpoint quando si aggiunge o si modifica una replica di disponibilità &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
 **'**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica un URL per definire un URL di endpoint o un URL di routing di sola lettura. I parametri URL sono i seguenti:  
  
 *system-address*  
 Stringa, ad esempio un nome di sistema, un nome di dominio completo o un indirizzo IP, che identifica in modo univoco il computer di destinazione.  
  
 *port*  
 Numero di porta associato all'endpoint del mirroring dell'istanza del server partner (per l'opzione ENDPOINT_URL) o numero di porta utilizzato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] dell'istanza del server (per l'opzione READ_ONLY_ROUTING_URL).  
  
 AVAILABILITY_MODE  **=**  {{SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT | CONFIGURATION_ONLY}  
 SYNCHRONOUS_COMMIT o ASYNCHRONOUS_COMMIT specifica se la replica primaria deve attendere la replica secondaria per l'accettazione della finalizzazione (scrittura) dei record del log su disco prima che la replica primaria può eseguire il commit della transazione in una determinato primaria database. Il commit delle transazioni in database diversi della stessa replica primaria può essere eseguito indipendentemente. Aggiornamento Cumulativo 1 di SQL Server 2017 introduce CONFIGURATION_ONLY. Replica CONFIGURATION_ONLY si applica solo ai gruppi di disponibilità con CLUSTER_TYPE = esterno o CLUSTER_TYPE = NONE. 
  
 SYNCHRONOUS_COMMIT  
 Specifica che la replica primaria eseguirà il commit delle transazioni solo dopo la finalizzazione nella replica secondaria (modalità con commit sincrono). È possibile specificare SYNCHRONOUS_COMMIT per un massimo di tre repliche, inclusa la replica primaria.  
  
 ASYNCHRONOUS_COMMIT  
 Specifica che la replica primaria esegue il commit delle transazioni senza attendere la finalizzazione del log da parte della replica secondaria (modalità di disponibilità con commit sincrono). È possibile specificare ASYNCHRONOUS_COMMIT per un massimo di cinque repliche di disponibilità, inclusa la replica primaria.  

 CONFIGURATION_ONLY specifica che la replica primaria commit in modo sincrono i metadati di configurazione gruppo di disponibilità al database master in questa replica. La replica non conterrà dati utente. Questa opzione:

- Possono essere ospitati in qualsiasi edizione di SQL Server Express Edition.
- Richiede che i dati di endpoint del mirroring della replica CONFIGURATION_ONLY tipo `WITNESS`.
- Non può essere modificato.
- Non è valido quando `CLUSTER_TYPE = WSFC`. 

   Per ulteriori informazioni, vedere [replica solo configurazione](../../linux/sql-server-linux-availability-group-ha.md).
  
 La clausola AVAILABILITY_MODE è obbligatoria. Per altre informazioni, vedere [Modalità di disponibilità &#40;gruppi di disponibilità AlwaysOn&#41;](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
 FAILOVER_MODE  **=**  {AUTOMATICO | MANUALE}  
 Specifica la modalità di failover della replica di disponibilità che si sta definendo.  
  
 AUTOMATIC  
 Abilita il failover automatico. Questa opzione è supportata solo se si specifica anche AVAILABILITY_MODE = SYNCHRONOUS_COMMIT. È possibile specificare AUTOMATIC per due repliche di disponibilità, inclusa la replica primaria.  
  
> [!NOTE]  
>  Le istanze del cluster di failover di SQL Server non supportano il failover automatico da gruppi di disponibilità, pertanto le replica di disponibilità ospitate da un'istanza del cluster di failover possono essere configurate solo per il failover manuale.  
  
 MANUAL  
 Consente il failover manuale pianificato o failover manuale forzato (in genere chiamato *failover forzato*) dall'amministratore del database.  
  
 La clausola FAILOVER_MODE è obbligatoria. I due tipi di failover manuale, failover manuale senza perdita di dati e failover forzato (con possibile perdita di dati), sono supportati a seconda delle diverse condizioni. Per altre informazioni, vedere [Failover e modalità di failover &#40;gruppi di disponibilità AlwaysOn&#41;](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md).  
  
 SEEDING_MODE  **=**  {AUTOMATICO | MANUALE}  
 Specifica come la replica secondaria è inizialmente di seeding.  
  
 AUTOMATIC  
 Abilita il seeding diretto. Questo metodo esegue il seeding della replica secondaria in rete. Questo metodo non richiede di eseguire il backup e ripristinare una copia del database primario sulla replica.  
  
> [!NOTE]  
>  Per il seeding diretto, è necessario consentire la creazione del database in ogni replica secondaria chiamando **ALTER AVAILABILITY GROUP** con il **GRANT CREATE ANY DATABASE** opzione.  
  
 MANUAL  
 Specifica il seeding manuale (impostazione predefinita). Questo metodo è necessario creare un backup del database nella replica primaria e ripristinare manualmente il backup nella replica secondaria.  
  
 BACKUP_PRIORITY  **=** *n*  
 Specifica la priorità di esecuzione dei backup nella replica rispetto alle altre repliche nello stesso gruppo di disponibilità. Il valore è un numero intero compreso nell'intervallo 0-100. I valori hanno il significato seguente:  
  
-   1..100 indica che la replica di disponibilità potrebbe essere scelta per l'esecuzione dei backup. 1 indica la priorità più bassa e 100 indica la priorità più alta. Se BACKUP_PRIORITY = 1, la replica di disponibilità verrà scelta per l'esecuzione dei backup solo se non sono attualmente disponibili repliche di disponibilità con priorità più alta.  
  
-   0 indica che questa replica di disponibilità non è impostato per l'esecuzione di backup. Ciò si rivela utile, ad esempio, per una replica di disponibilità remota in cui non si desidera eseguire mai il failover dei backup.  
  
 Per altre informazioni, vedere [Repliche secondarie attive: Backup in repliche secondarie &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
 SECONDARY_ROLE **(** ... **)**  
 Specifica le impostazioni specifiche del ruolo che avranno effetto se la replica di disponibilità è attualmente assegnato il ruolo secondario (ovvero, ogni volta che si tratta di una replica secondaria). All'interno delle parentesi, specificare uno o entrambe opzioni per il ruolo secondario. Se si specificano entrambe, usare un elenco delimitato da virgole.  
  
 Le opzioni per il ruolo secondario sono le seguenti:  
  
 ALLOW_CONNECTIONS  **=**  {N | READ_ONLY | TUTTI I}  
 Specifica se i database di una determinata replica di disponibilità che esegue il ruolo secondario, ovvero che funge da replica secondaria, possono accettare connessioni dai client, ovvero:  
  
 NO  
 Non sono consentite connessioni utente ai database secondari di questa replica. I database non sono disponibili per l'accesso in lettura. Questo è il comportamento predefinito.  
  
 READ_ONLY  
 Sono consentite solo connessioni ai database nella replica secondaria in cui impostare la proprietà Application Intent **ReadOnly**. Per altre informazioni su questa proprietà, vedere [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 ALL  
 Sono consentite tutte le connessioni ai database nella replica secondaria per l'accesso in sola lettura.  
  
 Per altre informazioni, vedere [Repliche secondarie attive: Repliche secondarie leggibili &#40;Gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 READ_ONLY_ROUTING_URL **='**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica l'URL da usare per il routing delle richieste di connessione con finalità di lettura a questa replica di disponibilità. Si tratta dell'URL sul quale è in ascolto il motore di database di SQL Server. In genere, l'istanza predefinita del motore di database di SQL Server è in ascolto sulla porta TCP 1433.  
  
 Per un'istanza denominata, è possibile ottenere il numero di porta eseguendo una query di **porta** e **type_desc** colonne di [tcp_listener_states](../../relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql.md) vista a gestione dinamica. L'istanza del server utilizza il listener Transact-SQL (**type_desc = 'TSQL'**).  
  
 Per ulteriori informazioni sul calcolo dell'URL di routing di sola lettura per una replica, vedere [calcolo di read_only_routing_url per Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-AlwaysOn.aspx).  
  
> [!NOTE]  
>  Per un'istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il listener Transact-SQL deve essere configurato per usare una porta specifica. Per altre informazioni, vedere [Configurazione di un server per l'attesa su una porta TCP specifica &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
 PRIMARY_ROLE **(** ... **)**  
 Specifica le impostazioni specifiche del ruolo che avranno effetto se la replica di disponibilità attualmente detiene il ruolo primario (ovvero, ogni volta che viene eseguita la replica primaria). All'interno delle parentesi, specificare uno o entrambe opzioni per il ruolo primario. Se si specificano entrambe, usare un elenco delimitato da virgole.  
  
 Le opzioni per il ruolo primario sono le seguenti:  
  
 ALLOW_CONNECTIONS  **=**  {READ_WRITE | TUTTI I}  
 Specifica il tipo di connessione che i database di una determinata replica di disponibilità che esegue il ruolo primario, ovvero che funge da replica primaria, possono accettare dai client, tra cui:  
  
 READ_WRITE  
 Non sono consentite le connessioni in cui la proprietà di connessione Finalità dell'applicazione è impostata su **Sola lettura** .  Se la proprietà Finalità dell'applicazione è impostata su **Lettura/Scrittura** o se tale proprietà non è impostata, la connessione è consentita. Per altre informazioni sulla proprietà di connessione Finalità dell'applicazione, vedere [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 ALL  
 Sono consentite tutte le connessioni ai database nella replica primaria. Questo è il comportamento predefinito.  
  
 READ_ONLY_ROUTING_LIST  **=**  { **('**\<istanza_server >**'** [ **,**... *n* ] **)** | NONE} Specifica un elenco delimitato da virgole di istanze del server che ospitano repliche di disponibilità per questo gruppo di disponibilità che soddisfano i requisiti seguenti durante l'esecuzione nel ruolo secondario:  
  
-   Sono configurate per consentire tutte le connessioni o connessioni in sola lettura (vedere l'argomento ALLOW_CONNECTIONS dell'opzione SECONDARY_ROLE, sopra).  
  
-   Dispongono del proprio URL del routing di sola lettura (vedere l'argomento READ_ONLY_ROUTING_URL dell'opzione SECONDARY_ROLE, sopra).  
  
 I valori di READ_ONLY_ROUTING_LIST sono i seguenti:  
  
 \<istanza_server > specifica l'indirizzo dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è l'host per una replica che è una replica secondaria leggibile quando viene eseguito nel ruolo secondario.  
  
 Usare un elenco delimitato da virgole per specificare tutte le istanze del server che potrebbero ospitare una replica secondaria leggibile. Routing di sola lettura seguirà l'ordine nel quale server le istanze vengono specificate nell'elenco. Se si include l'istanza del server host di una replica nell'elenco di routing di sola lettura della replica, il posizionamento di questa istanza del server alla fine dell'elenco costituisce in genere buona pratica, poiché le connessioni con finalità di lettura vengono indirizzate a una replica secondaria, se ne è disponibile una.  
  
 A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], le richieste di bilanciamento del carico con finalità di lettura è possibile tra le repliche secondarie leggibili. Specificare inserendo le repliche in un set annidato di parentesi all'interno dell'elenco di routing di sola lettura. Per ulteriori informazioni ed esempi, vedere [configurare il bilanciamento del carico tra le repliche di sola lettura](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing).  
  
 Nessuno  
 Specifica che quando questa replica di disponibilità è la replica primaria, il routing di sola lettura non è supportato. Questo è il comportamento predefinito.  
  
 SESSION_TIMEOUT  **=**  *integer*  
 Specifica il periodo di timeout della sessione in secondi. Se non si specifica questa opzione, il periodo di timeout predefinito è di 10 secondi. Il valore minimo è 5 secondi.  
  
> [!IMPORTANT]  
>  È consigliabile usare un periodo di timeout di almeno 10 secondi.  
  
 Per ulteriori informazioni sul periodo di timeout della sessione, vedere [Panoramica di gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
 GRUPPO DI DISPONIBILITÀ IN  
 Specifica i due gruppi di disponibilità che costituiscono un *gruppo di disponibilità distribuito*. Ogni gruppo di disponibilità fa parte di un proprio Server Failover Cluster WSFC (Windows). Quando si crea un gruppo di disponibilità distribuito, gruppo di disponibilità nell'istanza di SQL Server corrente diventa il gruppo di disponibilità primaria. Il secondo gruppo di disponibilità diventa il gruppo di disponibilità secondaria.  
  
 È necessario aggiungere il gruppo di disponibilità secondaria al gruppo di disponibilità distribuito. Per altre informazioni, vedere [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
 \<ag_name > specifica il nome del gruppo di disponibilità che costituisce una parte del gruppo di disponibilità distribuito.  
  
 LISTENER **='**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica il percorso URL per il listener associato al gruppo di disponibilità.  
  
 La clausola LISTENER è obbligatoria.  
  
 **'**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica un URL per il listener associato al gruppo di disponibilità. I parametri URL sono i seguenti:  
  
 *system-address*  
 È una stringa, ad esempio un nome di sistema, un nome di dominio completo o un indirizzo IP, che identifica in modo univoco il listener.  
  
 *port*  
 È un numero di porta associato all'endpoint del mirroring del gruppo di disponibilità. Si noti che questo non è la porta del listener.  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT | CONFIGURATION_ONLY}  
 Specifica se la replica primaria deve rimanere in attesa per il gruppo di disponibilità secondaria per l'accettazione della finalizzazione (scrittura) dei record del log su disco prima che la replica primaria può eseguire il commit della transazione in un determinato database primario.  
  
 SYNCHRONOUS_COMMIT  
 Specifica che la replica primaria eseguirà il commit delle transazioni fino a quando non sono stati salvati nel gruppo di disponibilità secondaria. È possibile specificare SYNCHRONOUS_COMMIT per un massimo di due gruppi di disponibilità, incluso il gruppo di disponibilità primaria.  
  
 ASYNCHRONOUS_COMMIT  
 Specifica che la replica primaria esegue il commit delle transazioni senza attendere per il gruppo di disponibilità secondaria per finalizzare il log. È possibile specificare ASYNCHRONOUS_COMMIT per un massimo di due gruppi di disponibilità, incluso il gruppo di disponibilità primaria.  
  
 La clausola AVAILABILITY_MODE è obbligatoria.  
  
 FAILOVER_MODE  **=**  {MANUALE}  
 Specifica la modalità di failover del gruppo di disponibilità distribuito.  
  
 MANUAL  
 Consente il failover manuale pianificato o failover manuale forzato (in genere chiamato *failover forzato*) dall'amministratore del database.  
  
 La clausola FAILOVER_MODE è obbligatoria e l'unica opzione è manuale. Il failover automatico sul gruppo di disponibilità secondario non è supportato.  
  
 SEEDING_MODE  **=**  {AUTOMATICO | MANUALE}  
 Specifica la modalità gruppo di disponibilità secondario è inizialmente di seeding.  
  
 AUTOMATIC  
 Abilita il seeding diretto. Questo metodo esegue il seeding del gruppo di disponibilità secondaria in rete. Questo metodo non richiede di eseguire il backup e ripristinare una copia del database primario nelle repliche del gruppo di disponibilità secondaria.  
  
 MANUAL  
 Specifica il seeding manuale (impostazione predefinita). Questo metodo è necessario creare un backup del database nella replica primaria e ripristinare manualmente il backup su repliche del gruppo di disponibilità secondaria.  
  
 LISTENER **'***dns_name***' (** \<opzione_listener > **)** definisce un nuovo listener del gruppo di disponibilità per questo gruppo di disponibilità. LISTENER è un argomento facoltativo.  
  
> [!IMPORTANT]  
>  Prima di creare il primo listener, è consigliabile leggere [creare o configurare un listener del gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
>   
>  Dopo aver creato un listener per un gruppo di disponibilità specifico, è consigliabile effettuare le operazioni seguenti:  
>   
>  -   Chiedere all'amministratore di rete di riservare l'indirizzo IP del listener per un uso esclusivo.  
> -   Fornire il nome host DNS del listener agli sviluppatori dell'applicazione in modo da essere usato nelle stringhe di connessione per la richiesta di connessioni client al gruppo di disponibilità.  
  
 *dns_name*  
 Specifica il nome host DNS del listener del gruppo di disponibilità. È necessario che il nome DNS del listener sia univoco nel dominio e in NetBIOS.  
  
 *dns_name* è un valore stringa. Può contenere solo caratteri alfanumerici, trattini (-) e caratteri di sottolineatura (_), in qualsiasi ordine. Per i nomi host DNS non viene fatta distinzione tra maiuscole e minuscole. La lunghezza massima è di 63 caratteri.  
  
 È consigliabile specificare una stringa significativa. Ad esempio, per un gruppo di disponibilità denominato `AG1`un nome host DNS significativo potrebbe essere `ag1-listener`.  
  
> [!IMPORTANT]  
>  NetBIOS riconosce solo i primi 15 caratteri di dns_name. Se si dispone di due cluster WSFC controllati dalla stessa Active Directory e si tenta di creare listener del gruppo di disponibilità in entrambi i cluster usando nomi con più di 15 caratteri e un prefisso di 15 caratteri identico, un errore segnala che di rete virtuale Nome risorsa non è possibile portare online. Per informazioni sulle regole di denominazione dei prefissi per i nomi DNS, vedere [Assegnare nomi ai domini](http://technet.microsoft.com/library/cc731265\(WS.10\).aspx).  
  
 \<opzione_listener > LISTENER accetta uno dei seguenti \<opzione_listener > opzioni: 
  
 CON DHCP [ON { **('***four_part_ipv4_address***','***four_part_ipv4_mask***')** }]  
 Specifica che il listener del gruppo di disponibilità Usa Dynamic Host Configuration Protocol (DHCP).  Facoltativamente, è possibile utilizzare la clausola ON per identificare la rete in cui viene creato il listener. DHCP è limitato a una sola subnet viene utilizzata per tutte le istanze del server che ospita una replica nel gruppo di disponibilità.  
  
> [!IMPORTANT]  
>  Non è consigliabile utilizzare DHCP negli ambienti di produzione. Se si verifica un periodo di inattività e il lease IP DHCP scade, è necessario del tempo aggiuntivo per registrare il nuovo indirizzo IP della rete DHCP che è associato al nome DNS del listener e influisce sulla connettività client. DHCP può essere tranquillamente usato per la configurazione dell'ambiente di sviluppo e test per verificare le funzioni di base di gruppi di disponibilità e per l'integrazione con le applicazioni.  
  
 Esempio:  
  
 `WITH DHCP ON ('10.120.19.0','255.255.254.0')`  
  
 CON IP **(** { **('***four_part_ipv4_address***','***four_part_ipv4_mask* **')** | **('***ipv6_address***')** } [ **,** ...  *n*  ] **)** [ **,** Porta  **=**  *listener_port* ]  
 Specifica che, anziché usare DHCP, il listener del gruppo di disponibilità utilizzerà uno o più indirizzi IP statici. Per creare un gruppo di disponibilità tra più subnet, viene richiesto un indirizzo IP statico nella configurazione del listener per ogni subnet. Per una determinata subnet, l'indirizzo IP statico può essere un indirizzo IPv4 o IPv6. Contattare l'amministratore di rete per ottenere un indirizzo IP statico per ogni subnet che ospita una replica per il nuovo gruppo di disponibilità.  
  
 Esempio:  
  
 `WITH IP ( ('10.120.19.155','255.255.254.0') )`  
  
 *four_part_ipv4_address*  
 Specifica un indirizzo IPv4 in quattro parti per un listener del gruppo di disponibilità, Ad esempio, `10.120.19.155`.  
  
 *four_part_ipv4_mask*  
 Specifica una maschera IPv4 in quattro parti per un listener del gruppo di disponibilità, Ad esempio, `255.255.254.0`.  
  
 *ipv6_address*  
 Specifica un indirizzo IPv6 per un listener del gruppo di disponibilità, Ad esempio, `2001::4898:23:1002:20f:1fff:feff:b3a3`.  
  
 PORTA  **=**  *listener_port*  
 Specifica il numero di porta:*listener_port*, utilizzabile da un listener del gruppo di disponibilità specificato da una clausola WITH IP. PORT è facoltativo.  
  
 È supportato il numero di porta predefinito, 1433. Tuttavia, per motivi di sicurezza, è consigliabile usare un numero di porta diverso.  
  
 Ad esempio: `WITH IP ( ('2001::4898:23:1002:20f:1fff:feff:b3a3') ) , PORT = 7777`  
  
## <a name="prerequisites-and-restrictions"></a>Prerequisiti e restrizioni  
 Per informazioni sui prerequisiti per la creazione di un gruppo di disponibilità, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 Per informazioni sulle restrizioni sulle istruzioni AVAILABILITY GROUP Transact-SQL, vedere [Cenni preliminari su istruzioni Transact-SQL per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/transact-sql-statements-for-always-on-availability-groups.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Sono necessarie l'appartenenza al ruolo predefinito del server **sysadmin** e l'autorizzazione server CREATE AVAILABILITY GROUP oppure l'autorizzazione ALTER ANY AVAILABILITY GROUP o CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-configuring-backup-on-secondary-replicas-flexible-failover-policy-and-connection-access"></a>A. Configurazione di un backup nelle repliche secondarie, dei criteri di failover flessibili e dell'accesso alla connessione  
 Nell'esempio seguente si crea un gruppo di disponibilità denominato `MyAg` per due database utente, `ThisDatabase` e `ThatDatabase`. Nella tabella seguente si riepilogano i valori specificati per le opzioni impostate per il gruppo di disponibilità.  
  
|Opzione del gruppo|Impostazione|Description|  
|------------------|-------------|-----------------|  
|AUTOMATED_BACKUP_PREFERENCE|SECONDARY|Con questa preferenza di backup automatico viene indicato che i backup devono essere eseguiti in una replica secondaria tranne quando la replica primaria è l'unica replica online (comportamento predefinito). Affinché l'impostazione AUTOMATED_BACKUP_PREFERENCE abbia effetto, è necessario generare script di processi di backup sui database di disponibilità per prendere in considerazione la preferenza di backup automatico.|  
|FAILURE_CONDITION_LEVEL|3|Con questa impostazione del livello della condizione di errore viene specificato che deve essere avviato un failover automatico in caso di errori interni di SQL Server critici, ad esempio spinlock orfani, gravi violazioni dell'accesso in scrittura o dumping eccessivo.|  
|HEALTH_CHECK_TIMEOUT|600000|Questo valore di timeout controllo integrità, 60 secondi, specifica che il cluster WSFC attende 60.000 millisecondi per il [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) stored procedure per restituire le informazioni di integrità del server che è un'istanza del server di sistema ospita una replica con commit sincrono con automatic prima che il cluster si presuppone che l'istanza del server host sia lenta o bloccata. Il valore predefinito è 30000 millisecondi.|  
  
 Tre repliche di disponibilità devono essere ospitate dalle istanze predefinite del server in computer denominati `COMPUTER01`, `COMPUTER02` e `COMPUTER03`. Nella tabella seguente si riepilogano i valori specificati per le opzioni di ogni replica.  
  
|Opzione della replica|Impostazione su `COMPUTER01`|Impostazione su `COMPUTER02`|Impostazione su `COMPUTER03`|Description|  
|--------------------|-----------------------------|-----------------------------|-----------------------------|-----------------|  
|ENDPOINT_URL|TCP: / /*COMPUTER01:5022*|TCP: / /*COMPUTER02:5022*|TCP: / /*COMPUTER03:5022*|In questo esempio i sistemi si trovano nello stesso dominio, pertanto per gli URL dell'endpoint può essere usato il nome del sistema come relativo indirizzo.|  
|AVAILABILITY_MODE|SYNCHRONOUS_COMMIT|SYNCHRONOUS_COMMIT|ASYNCHRONOUS_COMMIT|In due repliche viene usata la modalità con commit sincrono. In caso di sincronizzazione, supportano il failover senza perdita di dati. Nella terza replica viene usata la modalità di disponibilità con commit asincrono.|  
|FAILOVER_MODE|AUTOMATIC|AUTOMATIC|MANUAL|Le repliche con commit sincrono supportano il failover automatico e il failover manuale pianificato. La replica in cui viene usata la modalità di disponibilità con commit sincrono supporta solo il failover manuale forzato.|  
|BACKUP_PRIORITY|30|30|90|Alla replica con commit asincrono viene assegnata una priorità più alta, pari a 90, rispetto alle repliche con commit sincrono. I backup tendono a verificarsi nell'istanza del server che ospita la replica con commit asincrono.|  
|SECONDARY_ROLE|( ALLOW_CONNECTIONS = NO,<br /><br /> READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01:1433' )|( ALLOW_CONNECTIONS = NO,<br /><br /> READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02:1433' )|( ALLOW_CONNECTIONS = READ_ONLY, <br />READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03:1433' )|Solo la replica con commit asincrono viene usata come replica secondaria leggibile.<br /><br /> Specifica il nome del computer e il numero di porta predefinito del motore di database (1433).<br /><br /> L'argomento è facoltativo.|  
|PRIMARY_ROLE|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = (COMPUTER03) )|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = (COMPUTER03) )|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = NONE )|Nel ruolo primario, tutte le repliche rifiuta i tentativi di connessione con finalità di lettura.<br /><br /> Le richieste di connessione con finalità di lettura vengono indirizzate a COMPUTER03 se la replica locale è in esecuzione nel ruolo secondario. Quando tale replica è in esecuzione nel ruolo primario, il routing di sola lettura è disabilitato.<br /><br /> L'argomento è facoltativo.|  
|SESSION_TIMEOUT|10|10|10|In questo esempio si specifica il valore di timeout della sessione predefinito (10). L'argomento è facoltativo.|  
  
 Infine, nell'esempio si specificano la clausola LISTENER facoltativa per creare un listener per il nuovo gruppo di disponibilità e un nome DNS univoco, `MyAgListenerIvP6`, per questo listener. Le due repliche si trovano in subnet diverse, pertanto per il listener devono essere usati indirizzi IP statici. Per ognuna delle due repliche di disponibilità, tramite la clausola WITH IP si specifica un indirizzo IP statico, `2001:4898:f0:f00f::cf3c` e `2001:4898:e0:f213::4ce2`, per il quale è utilizzato il formato IPv6. In questo esempio si specifica anche utilizza l'argomento PORT facoltativo per indicare la porta `60173` come porta del listener.  
  
```SQL
CREATE AVAILABILITY GROUP MyAg   
   WITH (  
      AUTOMATED_BACKUP_PREFERENCE = SECONDARY,  
      FAILURE_CONDITION_LEVEL  =  3,   
      HEALTH_CHECK_TIMEOUT = 600000  
       )  
  
   FOR   
      DATABASE  ThisDatabase, ThatDatabase   
   REPLICA ON   
      'COMPUTER01' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC,  
         BACKUP_PRIORITY = 30,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = NO,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01:1433' ),
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER03) ),  
         SESSION_TIMEOUT = 10  
         ),   
  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC,  
         BACKUP_PRIORITY = 30,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = NO,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER03) ),  
         SESSION_TIMEOUT = 10  
         ),   
  
      'COMPUTER03' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:5022',  
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
         FAILOVER_MODE =  MANUAL,  
         BACKUP_PRIORITY = 90,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = NONE ),  
         SESSION_TIMEOUT = 10  
         );
GO  
ALTER AVAILABIIITY GROUP [MyAg]
  ADD LISTENER ‘MyAgListenerIvP6’ ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
GO  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Usare la Creazione guidata gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Usare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Usare la Creazione guidata gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [DROP AVAILABILITY GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/drop-availability-group-transact-sql.md)   
 [Risolvere i problemi sempre sulla configurazione di gruppi di disponibilità &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)   
 [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  

