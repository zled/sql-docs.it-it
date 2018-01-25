---
title: ALTER AVAILABILITY GROUP (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/02/2018
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
- ALTER_AVAILABILITY_GROUP_TSQL
- ALTER_AVAILABILITY_TSQL
- ALTER AVAILABILITY GROUP
- ALTER AVAILABILITY
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- ALTER AVAILABILITY GROUP statement
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: f039d0de-ade7-4aaf-8b7b-d207deb3371a
caps.latest.revision: "152"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d9f18ee709fde7c9f239b08f553eaf43fad6e9d2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="alter-availability-group-transact-sql"></a>ALTER AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Modifica di un sempre nel gruppo di disponibilità in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La maggior parte degli argomenti ALTER AVAILABILITY GROUP sono supportati solo nella replica primaria corrente. Tuttavia gli argomenti JOIN, FAILOVER e FORCE_FAILOVER_ALLOW_DATA_LOSS sono supportati solo in repliche secondarie.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```SQL  
  
ALTER AVAILABILITY GROUP group_name   
  {  
     SET ( <set_option_spec> )   
   | ADD DATABASE database_name   
   | REMOVE DATABASE database_name  
   | ADD REPLICA ON <add_replica_spec>   
   | MODIFY REPLICA ON <modify_replica_spec>  
   | REMOVE REPLICA ON <server_instance>  
   | JOIN  
   | JOIN AVAILABILITY GROUP ON <add_availability_group_spec> [ ,...2 ]  
   | MODIFY AVAILABILITY GROUP ON <modify_availability_group_spec> [ ,...2 ]  
   | GRANT CREATE ANY DATABASE  
   | DENY CREATE ANY DATABASE  
   | FAILOVER  
   | FORCE_FAILOVER_ALLOW_DATA_LOSS   | ADD LISTENER ‘dns_name’ ( <add_listener_option> )  
   | MODIFY LISTENER ‘dns_name’ ( <modify_listener_option> )  
   | RESTART LISTENER ‘dns_name’  
   | REMOVE LISTENER ‘dns_name’  
   | OFFLINE  
  }  
[ ; ]  
  
<set_option_spec> ::=   
    AUTOMATED_BACKUP_PREFERENCE = { PRIMARY | SECONDARY_ONLY| SECONDARY | NONE }  
  | FAILURE_CONDITION_LEVEL  = { 1 | 2 | 3 | 4 | 5 }   
  | HEALTH_CHECK_TIMEOUT = milliseconds  
  | DB_FAILOVER  = { ON | OFF }   
  | REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = { integer }
  
<server_instance> ::=   
 { 'system_name[\instance_name]' | 'FCI_network_name[\instance_name]' }  
  
<add_replica_spec>::=  
  <server_instance> WITH  
    (  
       ENDPOINT_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT | CONFIGURATION_ONLY },  
       FAILOVER_MODE = { AUTOMATIC | MANUAL }   
       [ , <add_replica_option> [ ,...n ] ]  
    )   
  
  <add_replica_option>::=  
       SEEDING_MODE = { AUTOMATIC | MANUAL }   
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
          ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL }   
        | READ_ONLY_ROUTING_URL = 'TCP://system-address:port'   
          } )  
     | PRIMARY_ROLE ( {   
          ALLOW_CONNECTIONS = { READ_WRITE | ALL }   
        | READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE }   
          } )  
     | SESSION_TIMEOUT = seconds  
  
<modify_replica_spec>::=  
  <server_instance> WITH  
    (    
       ENDPOINT_URL = 'TCP://system-address:port'   
     | AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }   
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }   
     | SEEDING_MODE = { AUTOMATIC | MANUAL }   
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
          ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL }   
        | READ_ONLY_ROUTING_URL = 'TCP://system-address:port'   
          } )  
     | PRIMARY_ROLE ( {   
          ALLOW_CONNECTIONS = { READ_WRITE | ALL }   
        | READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE }   
          } )  
     | SESSION_TIMEOUT = seconds  
    )   
  
<add_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = MANUAL,  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<modify_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER = 'TCP://system-address:port'  
       | AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
       | SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<add_listener_option> ::=  
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
  
<modify_listener_option>::=  
    {  
       ADD IP ( <ip_address_option> )   
     | PORT = listener_port  
    }  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *group_name*  
 Specifica il nome del nuovo gruppo di disponibilità. *nome_gruppo* deve essere un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore e deve essere univoco in tutti i gruppi di disponibilità nel cluster WSFC.  
  
 AUTOMATED_BACKUP_PREFERENCE  **=**  {PRIMARIO | SECONDARY_ONLY | SECONDARIO | NONE}  
 Specifica le preferenze per la modalità di valutazione della replica primaria da parte di un processo di backup nella scelta della posizione in cui eseguire i backup. È possibile generare uno script affinché un processo di backup specifico prenda in considerazione le preferenze di backup automatico. È importante comprendere che la preferenza non viene applicata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pertanto non incide sui backup ad hoc.  
  
 Supportato solo nella replica primaria.  
  
 Sono disponibili i valori seguenti:  
  
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
>  Non è prevista l'applicazione dell'impostazione AUTOMATED_BACKUP_PREFERENCE. L'interpretazione di questa preferenza dipende dall'eventuale logica su cui si basano gli script dei processi di backup per i database in un determinato gruppo di disponibilità. L'impostazione delle preferenze di backup automatico non incide sui backup ad hoc. Per ulteriori informazioni, vedere [configurare il Backup su repliche di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
> [!NOTE]  
>  Per visualizzare la preferenza di backup automatico di un gruppo di disponibilità esistente, selezionare il **automated_backup_preference** o **automated_backup_preference_desc** colonna il [ availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) vista del catalogo. Inoltre, [Sys. fn_hadr_backup_is_preferred_replica &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md) può essere usato per determinare la replica di backup preferita.  Questa funzione restituirà sempre 1 per almeno una delle repliche, anche quando `AUTOMATED_BACKUP_PREFERENCE = NONE`.  
  
 FAILURE_CONDITION_LEVEL  **=**  {1 | 2 | **3** | 4 | 5}  
 Specifica le condizioni di errore che attivano un failover automatico per il gruppo di disponibilità. FAILURE_CONDITION_LEVEL viene impostato a livello di gruppo ma è rilevante solo sulle repliche di disponibilità sono configurate per la modalità di disponibilità con commit sincrono (AVAILIBILITY_MODE  **=**  SYNCHRONOUS_COMMIT). Inoltre, le condizioni di errore possono attivare un failover automatico solo se entrambe le repliche primarie e secondarie sono configurate per la modalità di failover automatico (FAILOVER_MODE  **=**  automatico) e la replica secondaria è attualmente sincronizzata con la replica primaria.  
  
 Supportato solo nella replica primaria.  
  
 I livelli delle condizioni di errore (1-5) vanno dal livello 1, meno restrittivo, al livello 5, più restrittivo. Un livello della condizione specifico include tutti i livelli meno restrittivi. Il livello della condizione più restrittivo, ovvero il livello 5, include pertanto i quattro livelli della condizione meno restrittivi (1-4), il livello 4 include i livelli 1-3 e così via. Nella tabella seguente viene descritta la condizione di errore che corrisponde a ciascun livello.  
  
|Level|Condizione di errore|  
|-----------|-----------------------|  
|1|Specifica che deve essere avviato un failover automatico quando si verifica una delle condizioni seguenti:<br /><br /> Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è attivo.<br /><br /> Il lease del gruppo di disponibilità per la connessione al cluster WSFC scade poiché non viene ricevuto alcun acknowledgement dall'istanza del server. Per altre informazioni, vedere [Funzionamento: timeout lease di SQL Server Always On](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx).|  
|2|Specifica che deve essere avviato un failover automatico quando si verifica una delle condizioni seguenti:<br /><br /> L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non si connette al cluster e viene superata la soglia HEALTH_CHECK_TIMEOUT specificata dall'utente del gruppo di disponibilità.<br /><br /> La replica di disponibilità si trova in uno stato di errore.|  
|3|Specifica che deve essere avviato un failover automatico in caso di errori interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] critici, ad esempio spinlock orfani, gravi violazioni dell'accesso in scrittura o dumping eccessivo.<br /><br /> Questo è il comportamento predefinito.|  
|4|Specifica che deve essere avviato un failover automatico in caso di errori interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con gravità moderata, ad esempio una condizione persistente di memoria insufficiente nel pool di risorse interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|5|Specifica che deve essere avviato un failover automatico in caso di qualsiasi condizione di errore qualificata, tra cui:<br /><br /> Esaurimento dei thread di lavoro del motore SQL.<br /><br /> Rilevamento di un deadlock irrisolvibile.|  
  
> [!NOTE]  
>  L'assenza di risposta da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle richieste del client non è rilevante per i gruppi di disponibilità.  
  
 I valori FAILURE_CONDITION_LEVEL e HEALTH_CHECK_TIMEOUT, definire un *criteri di failover flessibili* per un gruppo specifico. fornendo un controllo granulare sulle condizioni che devono causare un failover automatico. Per ulteriori informazioni, vedere [criteri di Failover flessibili per Failover automatico di un gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/flexible-automatic-failover-policy-availability-group.md).  
  
 HEALTH_CHECK_TIMEOUT  **=**  *millisecondi*  
 Specifica il tempo di attesa (in millisecondi) per il [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) sistema stored procedure per restituire informazioni sull'integrità del server prima che il cluster WSFC si presuppone che l'istanza del server sia lenta o bloccata. HEALTH_CHECK_TIMEOUT viene impostato a livello di gruppo ma è rilevante solo sulle repliche di disponibilità che sono configurate per la modalità di disponibilità con commit sincrono con failover automatico (AVAILIBILITY_MODE  **=**  SINCRONO _COMMIT).  Inoltre, un timeout controllo integrità può attivare un failover automatico solo se entrambe le repliche primarie e secondarie sono configurate per la modalità di failover automatico (FAILOVER_MODE  **=**  automatico) e il database secondario replica è attualmente sincronizzata con la replica primaria.  
  
 Il valore predefinito di HEALTH_CHECK_TIMEOUT è 30000 millisecondi (30 secondi). Il valore minimo è 15000 millisecondi (15 secondi) e il valore massimo è 4294967295 millisecondi.  
  
 Supportato solo nella replica primaria.  
  
> [!IMPORTANT]  
>  **sp_server_diagnostics** non esegue controlli di integrità a livello di database.  
  
 DB_FAILOVER  **=**  {ON | OFF}  
 Specifica la risposta da intraprendere quando un database nella replica primaria è offline. Quando è impostata su ON, qualsiasi stato diverso da in linea per un database nel gruppo di disponibilità viene attivato un failover automatico. Quando questa opzione è impostata su OFF, solo l'integrità dell'istanza viene utilizzato per attivare il failover automatico.  
 
 Per ulteriori informazioni su questa impostazione, vedere [opzione di rilevamento dello stato di livello Database](../../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md) 

 
 REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT   
 Introdotti in SQL Server 2017. Utilizzato per impostare un numero minimo di repliche secondarie sincrone necessarie per eseguire il commit prima che il database primario viene eseguito il commit di una transazione. Garantisce che le transazioni di SQL Server rimarrà in attesa fino a quando non vengono aggiornati i log delle transazioni per il numero minimo delle repliche secondarie. Il valore predefinito è 0, che fornisce lo stesso comportamento di SQL Server 2016. Il valore minimo è 0. Il valore massimo è il numero di repliche meno 1. Questa opzione mette in relazione alle repliche in modalità con commit sincrono. Durante le repliche sono in modalità con commit sincrono, scritture nella replica primaria attendere scritture sulle repliche secondarie sincrone vengano eseguito il commit nel log delle transazioni del database di replica. Se un Server SQL che ospita una replica sincrona secondaria si blocca, SQL Server che ospita la replica primaria viene contrassegnato che la replica secondaria come non SINCRONIZZATA e continuare. Quando il database non rispondono torna alla modalità online sarà in uno stato "not synced" e la replica verrà contrassegnata come non integro fino a quando il database primario può rendere sincroni nuovamente. Questa impostazione garantisce che la replica primaria non sarà possibile proseguire fino a quando il numero minimo di repliche è eseguito il commit di ogni transazione. Se il numero minimo delle repliche non è disponibile, commit sul database primario avrà esito negativo. Per il tipo di cluster `EXTERNAL` l'impostazione viene modificata quando il gruppo di disponibilità viene aggiunta a una risorsa cluster. Vedere [elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](../../linux/sql-server-linux-availability-group-ha.md).
  
 Aggiungi DATABASE *database_name*  
 Specifica un elenco di uno o più database utente che si desidera aggiungere al gruppo di disponibilità. Tali database devono risiedere nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui è ospitata la replica primaria corrente. È possibile specificare più database per un gruppo di disponibilità, ma ogni database può appartenere a un solo gruppo di disponibilità. Per informazioni sul tipo di database che può supportare un gruppo di disponibilità, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md). Per scoprire quali database locali già appartenenti a un gruppo di disponibilità, vedere il **replica_id** colonna il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
 Supportato solo nella replica primaria.  
  
> [!NOTE]  
>  Dopo aver creato il gruppo di disponibilità, sarà necessario connettersi a ogni istanza del server in cui è ospitata una replica secondaria, quindi preparare ciascun database secondario e aggiungerlo al gruppo di disponibilità. Per altre informazioni, vedere [Avviare lo spostamento dati su un database secondario Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
 Rimuovi DATABASE *database_name*  
 Rimuove il database primario specificato e i database secondari corrispondenti dal gruppo di disponibilità. Supportato solo nella replica primaria.  
  
 Per informazioni su consigliate da eseguire dopo la rimozione di un database di disponibilità da un gruppo di disponibilità, vedere [rimuovere un Database primario da un gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
 ADD REPLICA ON  
 Specifica da una a otto istanze di SQL Server per ospitare le repliche secondarie in un gruppo di disponibilità.  Ogni replica viene specificata dall'indirizzo della relativa istanza del server seguito da una clausola WITH (…).  
  
 Supportato solo nella replica primaria.  
  
 È necessario creare un join di ogni nuova replica secondaria al gruppo di disponibilità. Per altre informazioni, vedere la descrizione dell'opzione JOIN più avanti in questa sezione.  
  
 \<server_instance>  
 Specifica l'indirizzo dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è l'host per una replica. Il formato dell'indirizzo dipende dal fatto che l'istanza sia l'istanza predefinita o un'istanza denominata e se si tratti di un'istanza autonoma o un'istanza del cluster di failover (FCI). La sintassi è la seguente:  
  
 { '*_sistema*[\\*nome_istanza*]' | '*nome_rete_FCI*[\\*nome_istanza*]' }  
  
 I componenti di questo indirizzo sono i seguenti:  
  
 *_sistema*  
 Nome NetBIOS del computer in cui si trova l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il computer deve essere un nodo WSFC.  
  
 *nome_rete_FCI*  
 Nome di rete usato per accedere a un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Usare questo nome se l'istanza del server partecipa come partner di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'esecuzione di SELECT [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) in un'istanza FCI istanza del server restituisce l'intera '*nome_rete_fci*[\\*instance_name*]' stringa (che è la nome completo della replica).  
  
 *nome_istanza*  
 È il nome di un'istanza di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è ospitato da *nome_sistema* o *nome_rete_fci* e che disponga sempre abilitata. Per un'istanza del server predefinita, *nome_istanza* è facoltativo. Per il nome dell'istanza non viene fatta distinzione tra maiuscole e minuscole. In un'istanza del server autonomo, il nome del valore è uguale al valore restituito dall'esecuzione di SELECT [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md).  
  
 \  
 Separatore usato solo quando si specifica *instance_name*, per separarlo da *nome_sistema* o *nome_rete_fci*.  
  
 Per informazioni sui prerequisiti per i nodi WSFC e le istanze del server, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 ENDPOINT_URL ='TCP://*system-address*:*port*'  
 Specifica il percorso URL per il [endpoint del mirroring del database](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospiterà la replica di disponibilità che desidera aggiungere o modificare.  
  
 ENDPOINT_URL è obbligatorio nella clausola ADD REPLICA ON e facoltativo nella clausola MODIFY REPLICA ON.  Per altre informazioni, vedere [Specificare l'URL dell'Endpoint quando si aggiunge o modifica una Replica di disponibilità &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
 **'**TCP**://***system-address***:***port***'**  
 Specifica un URL per definire un URL di endpoint o un URL di routing di sola lettura. I parametri URL sono i seguenti:  
  
 *system-address*  
 Stringa, ad esempio un nome di sistema, un nome di dominio completo o un indirizzo IP, che identifica in modo univoco il computer di destinazione.  
  
 *port*  
 Numero di porta associato all'endpoint del mirroring dell'istanza del server (per l'opzione ENDPOINT_URL) o numero di porta usato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] dell'istanza del server (per l'opzione READ_ONLY_ROUTING_URL).  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT | CONFIGURATION_ONLY}  
 Specifica se la replica primaria deve attendere la conferma della finalizzazione (scrittura) dei record del log su disco da parte della replica secondaria prima di poter eseguire il commit della transazione in un database primario specifico. Il commit delle transazioni in database diversi della stessa replica primaria può essere eseguito indipendentemente.  
  
 SYNCHRONOUS_COMMIT  
 Specifica che la replica primaria esegue il commit delle transazioni solo dopo la finalizzazione nella replica secondaria (modalità con commit sincrono). È possibile specificare SYNCHRONOUS_COMMIT per un massimo di tre repliche, inclusa la replica primaria.  
  
 ASYNCHRONOUS_COMMIT  
 Specifica che la replica primaria esegue il commit delle transazioni senza attendere la finalizzazione del log da parte della replica secondaria (modalità di disponibilità con commit sincrono). È possibile specificare ASYNCHRONOUS_COMMIT per un massimo di cinque repliche di disponibilità, inclusa la replica primaria.  

 CONFIGURATION_ONLY specifica che la replica primaria commit in modo sincrono i metadati di configurazione gruppo di disponibilità al database master in questa replica. La replica non conterrà dati utente. Questa opzione:

- Possono essere ospitati in qualsiasi edizione di SQL Server Express Edition.
- Richiede che i dati di endpoint del mirroring della replica CONFIGURATION_ONLY tipo `WITNESS`.
- Non può essere modificato.
- Non è valido quando `CLUSTER_TYPE = WSFC`. 

   Per ulteriori informazioni, vedere [replica solo configurazione](../../linux/sql-server-linux-availability-group-ha.md).
    
 AVAILABILITY_MODE è obbligatorio nella clausola ADD REPLICA ON e facoltativo nella clausola MODIFY REPLICA ON. Per altre informazioni, vedere [Modalità di disponibilità &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
 FAILOVER_MODE  **=**  {AUTOMATICO | MANUALE}  
 Specifica la modalità di failover della replica di disponibilità che si sta definendo.  
  
 AUTOMATIC  
 Abilita il failover automatico. AUTOMATIC è supportato solo se si specifica anche AVAILABILITY_MODE = SYNCHRONOUS_COMMIT. È possibile specificare AUTOMATIC per due repliche di disponibilità, inclusa la replica primaria.  
  
> [!NOTE]  
>  Le istanze del cluster di failover di SQL Server non supportano il failover automatico da gruppi di disponibilità, pertanto le replica di disponibilità ospitate da un'istanza del cluster di failover possono essere configurate solo per il failover manuale.  
  
 MANUAL  
 Consente il failover manuale o failover manuale forzato (*failover forzato*) dall'amministratore del database.  
  
 FAILOVER_MODE è obbligatorio nella clausola ADD REPLICA ON e facoltativo nella clausola MODIFY REPLICA ON. Esistono due tipi di failover manuale, failover manuale senza perdita di dati e failover forzato (con possibile perdita di dati), supportati a seconda delle diverse condizioni.  Per altre informazioni, vedere [Failover e modalità di failover &#40;gruppi di disponibilità AlwaysOn&#41;](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md).  
  
 SEEDING_MODE  **=**  {AUTOMATICO | MANUALE}  
 Specifica come verrà seeding inizialmente la replica secondaria.  
  
 AUTOMATIC  
 Abilita il seeding diretto. Questo metodo eseguirà il seeding della replica secondaria in rete. Questo metodo non richiede di eseguire il backup e ripristinare una copia del database primario sulla replica.  
  
> [!NOTE]  
>  Per il seeding diretto, è necessario consentire la creazione del database in ogni replica secondaria chiamando **ALTER AVAILABILITY GROUP** con il **GRANT CREATE ANY DATABASE** opzione.  
  
 MANUAL  
 Specifica il seeding manuale (impostazione predefinita). Questo metodo è necessario creare un backup del database nella replica primaria e ripristinare manualmente il backup nella replica secondaria.  
  
 BACKUP_PRIORITY **=***n*  
 Specifica la priorità di esecuzione dei backup nella replica rispetto alle altre repliche nello stesso gruppo di disponibilità. Il valore è un numero intero compreso nell'intervallo 0-100. I valori hanno il significato seguente:  
  
-   1..100 indica che la replica di disponibilità potrebbe essere scelta per l'esecuzione dei backup. 1 indica la priorità più bassa e 100 indica la priorità più alta. Se BACKUP_PRIORITY = 1, la replica di disponibilità verrà scelta per l'esecuzione dei backup solo se non sono attualmente disponibili repliche di disponibilità con priorità più alta.  
  
-   0 indica che la replica di disponibilità non verrà mai scelta per l'esecuzione dei backup. Ciò si rivela utile, ad esempio, per una replica di disponibilità remota in cui non si desidera eseguire mai il failover dei backup.  
  
 Per altre informazioni, vedere [Repliche secondarie attive: Backup in repliche secondarie &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
 SECONDARY_ROLE **(** ... **)**  
 Specifica le impostazioni specifiche di ruolo che verranno applicate se questa replica di disponibilità è attualmente proprietaria del ruolo secondario (ovvero ogni volta che è una replica secondaria). All'interno delle parentesi, specificare uno o entrambe opzioni per il ruolo secondario. Se si specificano entrambe, usare un elenco delimitato da virgole.  
  
 Le opzioni per il ruolo secondario sono le seguenti:  
  
 ALLOW_CONNECTIONS  **=**  {N | READ_ONLY | TUTTI I}  
 Specifica se i database di una determinata replica di disponibilità che esegue il ruolo secondario, ovvero che funge da replica secondaria, possono accettare connessioni dai client, ovvero:  
  
 NO  
 Non sono consentite connessioni utente ai database secondari di questa replica. I database non sono disponibili per l'accesso in lettura. Questo è il comportamento predefinito.  
  
 READ_ONLY  
 Sono consentite solo connessioni ai database nella replica secondaria in cui impostare la proprietà Application Intent **ReadOnly**. Per altre informazioni su questa proprietà, vedere [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 ALL  
 Sono consentite tutte le connessioni ai database nella replica secondaria per l'accesso in sola lettura.  
  
 Per altre informazioni, vedere [Repliche secondarie attive: Repliche secondarie leggibili &#40;Gruppi di disponibilità AlwaysOn&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 READ_ONLY_ROUTING_URL **='**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica l'URL da usare per il routing delle richieste di connessione con finalità di lettura a questa replica di disponibilità. Si tratta dell'URL sul quale è in ascolto il motore di database di SQL Server. In genere, l'istanza predefinita del motore di database di SQL Server è in ascolto sulla porta TCP 1433.  
  
 Per un'istanza denominata, è possibile ottenere il numero di porta eseguendo una query di **porta** e **type_desc** colonne di [tcp_listener_states](../../relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql.md) vista a gestione dinamica. L'istanza del server utilizza il listener Transact-SQL (**type_desc = 'TSQL'**).  
  
 Per ulteriori informazioni sul calcolo dell'URL di routing di sola lettura per una replica di disponibilità, vedere [calcolo di read_only_routing_url per Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx).  
  
> [!NOTE]  
>  Per un'istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il listener Transact-SQL deve essere configurato per usare una porta specifica. Per altre informazioni, vedere [Configurazione di un server per l'attesa su una porta TCP specifica &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
 PRIMARY_ROLE **(** ... **)**  
 Specifica le impostazioni specifiche di ruolo che verranno applicate se questa replica di disponibilità è attualmente proprietaria del ruolo primario (ovvero ogni volta che è una replica primaria). All'interno delle parentesi, specificare uno o entrambe opzioni per il ruolo primario. Se si specificano entrambe, usare un elenco delimitato da virgole.  
  
 Le opzioni per il ruolo primario sono le seguenti:  
  
 ALLOW_CONNECTIONS  **=**  {READ_WRITE | TUTTI I}  
 Specifica il tipo di connessione che i database di una determinata replica di disponibilità che esegue il ruolo primario, ovvero che funge da replica primaria, possono accettare dai client, tra cui:  
  
 READ_WRITE  
 Non sono consentite le connessioni in cui la proprietà di connessione Finalità dell'applicazione è impostata su **Sola lettura** .  Se la proprietà Finalità dell'applicazione è impostata su **Lettura/Scrittura** o se tale proprietà non è impostata, la connessione è consentita. Per altre informazioni sulla proprietà di connessione Finalità dell'applicazione, vedere [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 ALL  
 Sono consentite tutte le connessioni ai database nella replica primaria. Questo è il comportamento predefinito.  
  
 READ_ONLY_ROUTING_LIST **=** { **(‘**\<server_instance>**’** [ **,**...*n* ] **)** | NONE }  
 Specifica un elenco delimitato da virgole di istanze del server in cui sono ospitate repliche di disponibilità per questo gruppo di disponibilità che soddisfano i requisiti seguenti quando vengono eseguite nel ruolo secondario:  
  
-   Sono configurate per consentire tutte le connessioni o connessioni in sola lettura (vedere l'argomento ALLOW_CONNECTIONS dell'opzione SECONDARY_ROLE, sopra).  
  
-   Dispongono del proprio URL del routing di sola lettura (vedere l'argomento READ_ONLY_ROUTING_URL dell'opzione SECONDARY_ROLE, sopra).  
  
 I valori di READ_ONLY_ROUTING_LIST sono i seguenti:  
  
 \<server_instance>  
 Specifica l'indirizzo dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che funge da host per una replica di disponibilità che è una replica secondaria leggibile quando è in esecuzione nel ruolo secondario.  
  
 Usare un elenco delimitato da virgole per specificare tutte le istanze del server che potrebbero ospitare una replica secondaria leggibile. Il routing di sola lettura seguirà l'ordine nel quale le istanze del server vengono specificate nell'elenco. Se si include l'istanza del server host di una replica nell'elenco di routing di sola lettura della replica, il posizionamento di questa istanza del server alla fine dell'elenco costituisce in genere buona pratica, poiché le connessioni con finalità di lettura vengono indirizzate a una replica secondaria, se ne è disponibile una.  
  
 A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], le richieste di bilanciamento del carico con finalità di lettura è possibile tra le repliche secondarie leggibili. Specificare inserendo le repliche in un set annidato di parentesi all'interno dell'elenco di routing di sola lettura. Per ulteriori informazioni ed esempi, vedere [configurare il bilanciamento del carico tra le repliche di sola lettura](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing).  
  
 Nessuno  
 Specifica che quando questa replica di disponibilità è la replica primaria, il routing di sola lettura non è supportato. Questo è il comportamento predefinito. In caso di utilizzo con MODIFY REPLICA ON, questo valore disabilita un elenco esistente, se presente.  
  
 SESSION_TIMEOUT **=***seconds*  
 Specifica il periodo di timeout della sessione in secondi. Se non si specifica questa opzione, il periodo di timeout predefinito è di 10 secondi. Il valore minimo è 5 secondi.  
  
> [!IMPORTANT]  
>  È consigliabile usare un periodo di timeout di almeno 10 secondi.  
  
 Per ulteriori informazioni sul periodo di timeout della sessione, vedere [Panoramica di gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
 MODIFY REPLICA ON  
 Modifica qualsiasi replica del gruppo di disponibilità. L'elenco di repliche da modificare contiene l'indirizzo dell'istanza del server e una clausola WITH (.) per ogni replica.  
  
 Supportato solo nella replica primaria.  
  
 REMOVE REPLICA ON  
 Rimuove la replica secondaria specificata dal gruppo di disponibilità. Non è possibile rimuovere la replica primaria corrente da un gruppo di disponibilità. Nel momento in cui viene rimossa, la replica non riceverà più i dati. I relativi database secondari vengono rimossi dal gruppo di disponibilità e viene attivato lo stato RESTORING.  
  
 Supportato solo nella replica primaria.  
  
> [!NOTE]  
>  Se si rimuove una replica mentre non è disponibile o si trova in stato di errore, quando torna alla modalità online rileverà di non appartenere più al gruppo di disponibilità.  
  
 JOIN  
 Consente all'istanza del server locale di ospitare una replica secondaria nel gruppo di disponibilità specificato.  
  
 Supportato solo in una replica secondaria non ancora aggiunta al gruppo di disponibilità.  
  
 Per altre informazioni, vedere [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
 FAILOVER  
 Avvia un failover manuale del gruppo di disponibilità senza perdita di dati nella replica secondaria a cui si è connessi. La replica in cui si immette un comando di failover di destinazione di failover è noto come il.  La destinazione di failover subentrerà al ruolo primario e recupererà la copia di ogni database per portarli online come nuovi database primari. La replica primaria precedente passa contemporaneamente al ruolo secondario e i relativi database diventano database secondari e vengono immediatamente sospesi. Potenzialmente, questi ruoli possono alternati in successione da una serie di errori.  
  
 Supportato solo su una replica secondaria con commit sincrono che è attualmente sincronizzata con la replica primaria. Notare che per la sincronizzazione di una replica secondaria, è necessario che anche la replica primaria sia in esecuzione in modalità con commit sincrono.  
  
> [!NOTE]  
>  Un comando di failover viene eseguito non appena la destinazione di failover avrà accettato il comando. Tuttavia, il recupero del database si verifica in modo asincrono dopo che il gruppo di disponibilità ha completato il failover.  
  
 Per informazioni sulle limitazioni, prerequisiti e consigli per l'esecuzione di un failover manuale pianificato, vedere [eseguire un Failover manuale pianificato di un gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
 FORCE_FAILOVER_ALLOW_DATA_LOSS  
 > [!CAUTION]  
>  L'uso forzato di un failover, che può comportare una perdita di dati, rappresenta esclusivamente un metodo di ripristino di emergenza. Pertanto, è consigliabile forzare il failover solo se la replica primaria non è più in esecuzione, si è disposti a rischiare la perdita di dati ed è necessario ripristinare immediatamente il servizio nel gruppo di disponibilità.  
  
 Supportato solo in una replica il cui ruolo è in uno stato SECONDARY o RESOLVING. -- La replica in cui si immette un comando di failover è nota come il *destinazione del failover*.  
  
 Forza il failover del gruppo di disponibilità, con possibile perdita di dati, nella destinazione di failover. La destinazione di failover subentrerà al ruolo primario e recupererà la copia di ogni database per portarli online come nuovi database primari. In tutte le repliche secondarie rimanenti, ogni database secondario viene sospeso finché non viene ripristinato manualmente. Quando la replica primaria precedente diventa disponibile, passerà al ruolo secondario e i relativi database diventeranno database secondari sospesi.  
  
> [!NOTE]  
>  Un comando di failover viene eseguito non appena la destinazione di failover avrà accettato il comando. Tuttavia, il recupero del database si verifica in modo asincrono dopo che il gruppo di disponibilità ha completato il failover.  
  
 Per informazioni sulle limitazioni, prerequisiti e consigli per il failover forzato e sull'effetto di un failover forzato sui database primari precedenti nel gruppo di disponibilità, vedere [eseguire un Failover manuale forzato di un di disponibilità Gruppo &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).  
  
 ADD LISTENER **'***dns_name***' (** \<add_listener_option > **)**  
 Definisce un nuovo listener per il gruppo di disponibilità. Supportato solo nella replica primaria.  
  
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
>  NetBIOS riconosce solo i primi 15 caratteri di dns_name. Se si dispone di due cluster WSFC controllati dallo stesso dominio Active Directory e si tenta di creare listener del gruppo di disponibilità in entrambi i cluster usando nomi con più di 15 caratteri e un prefisso a 15 caratteri identico, verrà restituito un errore in cui si segnala che non è possibile portare online la risorsa del nome di rete virtuale. Per informazioni sulle regole di denominazione dei prefissi per i nomi DNS, vedere [Assegnare nomi ai domini](http://technet.microsoft.com/library/cc731265\(WS.10\).aspx).  
  
 GRUPPO DI DISPONIBILITÀ DI JOIN IN  
 Crea un join tra una *gruppo di disponibilità distribuito*. Quando si crea un gruppo di disponibilità distribuito, il gruppo di disponibilità nel cluster in cui viene creato è il gruppo di disponibilità primaria. Il gruppo di disponibilità che esegue il join del gruppo di disponibilità distribuiti è il gruppo di disponibilità secondaria.  
  
 \<ag_name>  
 Specifica il nome del gruppo di disponibilità che costituisce una parte del gruppo di disponibilità distribuito.  
  
 LISTENER **='**TCP**://***indirizzo-sistema***:***porta***'**  
 Specifica il percorso URL per il listener associato al gruppo di disponibilità.  
  
 La clausola LISTENER è obbligatoria.  
  
 **'**TCP**://***system-address***:***port***'**  
 Specifica un URL per il listener associato al gruppo di disponibilità. I parametri URL sono i seguenti:  
  
 *system-address*  
 È una stringa, ad esempio un nome di sistema, un nome di dominio completo o un indirizzo IP, che identifica in modo univoco il listener.  
  
 *port*  
 È un numero di porta associato all'endpoint del mirroring del gruppo di disponibilità. Si noti che questo non è la porta del listener.  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT}  
 Specifica se la replica primaria deve rimanere in attesa per il gruppo di disponibilità secondaria per l'accettazione della finalizzazione (scrittura) dei record del log su disco prima che la replica primaria può eseguire il commit della transazione in un determinato database primario.  
  
 SYNCHRONOUS_COMMIT  
 Specifica che la replica primaria rimarrà in attesa per il commit delle transazioni fino a quando non sono stati salvati nel gruppo di disponibilità secondaria. È possibile specificare SYNCHRONOUS_COMMIT per un massimo di due gruppi di disponibilità, incluso il gruppo di disponibilità primaria.  
  
 ASYNCHRONOUS_COMMIT  
 Specifica che la replica primaria esegue il commit delle transazioni senza attendere per il gruppo di disponibilità secondaria per finalizzare il log. È possibile specificare ASYNCHRONOUS_COMMIT per un massimo di due gruppi di disponibilità, incluso il gruppo di disponibilità primaria.  
  
 La clausola AVAILABILITY_MODE è obbligatoria.  
  
 FAILOVER_MODE  **=**  {MANUALE}  
 Specifica la modalità di failover del gruppo di disponibilità distribuito.  
  
 MANUAL  
 Consente il failover manuale pianificato o failover manuale forzato (in genere chiamato *failover forzato*) dall'amministratore del database.  
  
 Il failover automatico sul gruppo di disponibilità secondario non è supportato.  
  
 SEEDING_MODE **=**  {AUTOMATICO | MANUALE}  
 Specifica come verrà seeding inizialmente il gruppo di disponibilità secondaria.  
  
 AUTOMATIC  
 Abilita il seeding automatico. Questo metodo eseguirà il seeding del gruppo di disponibilità secondaria in rete. Questo metodo non richiede di eseguire il backup e ripristinare una copia del database primario nelle repliche del gruppo di disponibilità secondaria.  
  
 MANUAL  
 Specifica il seeding manuale. Questo metodo è necessario creare un backup del database nella replica primaria e ripristinare manualmente il backup su repliche del gruppo di disponibilità secondaria.  
  
 MODIFICARE IL GRUPPO DI DISPONIBILITÀ IN  
 Modifica le impostazioni di gruppo di disponibilità di un gruppo di disponibilità distribuito. L'elenco di gruppi di disponibilità da modificare contiene il nome del gruppo di disponibilità e una con la clausola (...) per ogni gruppo di disponibilità.  
  
> [!IMPORTANT]  
>  Questo comando deve essere ripetuto sul gruppo di disponibilità primaria e le istanze di gruppo di disponibilità secondaria.  
  
 GRANT CREATE ANY DATABASE  
 Il gruppo di disponibilità per creare database per conto della replica primaria, che supporta il seeding diretto consente (SEEDING_MODE = AUTOMATIC). Questo parametro deve essere eseguito su ogni replica secondaria che supporta il seeding diretto dopo tale database secondario viene aggiunta al gruppo di disponibilità.  Richiede l'autorizzazione CREATE ANY DATABASE.  
  
 NEGARE CREATE ANY DATABASE  
 Rimuove il possibilità per creare database per conto della replica primaria del gruppo di disponibilità.  
  
 \<add_listener_option>  
 ADD LISTENER accetta una delle opzioni seguenti:  
  
 CON DHCP [ON { **('***four_part_ipv4_address***','***four_part_ipv4_mask***')** }]  
 Specifica che il listener del gruppo di disponibilità userà il protocollo DHCP (Dynamic Host Configuration Protocol).  Facoltativamente, utilizzare la clausola ON per identificare la rete su cui verrà creato il listener. DHCP è limitato a una sola subnet utilizzata per ogni istanza del server nel cui gruppo di disponibilità è ospitata una replica di disponibilità.  
  
> [!IMPORTANT]  
>  Non è consigliabile utilizzare DHCP negli ambienti di produzione. Se si verifica un periodo di inattività e il lease IP DHCP scade, è necessario del tempo aggiuntivo per registrare il nuovo indirizzo IP della rete DHCP che è associato al nome DNS del listener e influisce sulla connettività client. DHCP può essere tranquillamente usato per la configurazione dell'ambiente di sviluppo e test per verificare le funzioni di base di gruppi di disponibilità e per l'integrazione con le applicazioni.  
  
 Esempio:  
  
 `WITH DHCP ON ('10.120.19.0','255.255.254.0')`  
  
 CON IP **(** { **('***four_part_ipv4_address***','***four_part_ipv4_mask***')** | **('***ipv6_address***')** } [ **,** ...  *n*  ] **)** [ **,** Porta **= * * * listener_port* ]  
 Specifica che, anziché usare DHCP, nel listener del gruppo di disponibilità saranno usati uno o più indirizzi IP statici. Per creare un gruppo di disponibilità tra più subnet, viene richiesto un indirizzo IP statico nella configurazione del listener per ogni subnet. Per una determinata subnet, l'indirizzo IP statico può essere un indirizzo IPv4 o IPv6. Contattare l'amministratore di rete per ottenere un indirizzo IP statico per ogni subnet in cui verrà ospitata una replica di disponibilità per il nuovo gruppo di disponibilità.  
  
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
  
 Esempio: `WITH IP ( ('2001::4898:23:1002:20f:1fff:feff:b3a3') ) , PORT = 7777`  
  
 MODIFY LISTENER **'***dns_name***' (** \<modify_listener_option > **)**  
 Modifica un listener del gruppo di disponibilità esistente. Supportato solo nella replica primaria.  
  
 \<modify_listener_option>  
 MODIFY LISTENER accetta una delle opzioni seguenti:  
  
 ADD IP { **(‘***four_part_ipv4_address***’,‘***four_part_ipv4_mask***’)** | **(‘**dns_name*ipv6_address***’)** }  
 Aggiunge l'indirizzo IP specificato per il listener del gruppo di disponibilità specificato da *dns_name*.  
  
 PORTA  **=**  *listener_port*  
 Vedere la descrizione di questo argomento più indietro in questa sezione.  
  
 Riavviare LISTENER **'***dns_name***'**  
 Consente di riavviare il listener associato al nome DNS specificato. Supportato solo nella replica primaria.  
  
 Rimuovi LISTENER **'***dns_name***'**  
 Consente di rimuovere il listener associato al nome DNS specificato. Supportato solo nella replica primaria.  
  
 OFFLINE  
 Porta offline un gruppo di disponibilità online. Non si verifica alcuna perdita di dati per i database con commit sincrono.  
  
 Dopo aver portato un gruppo di disponibilità offline, i relativi database non saranno più disponibili per i client e non sarà possibile riportare nuovamente online il gruppo di disponibilità. Usare pertanto l'opzione OFFLINE solo durante la migrazione tra cluster di [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], se si esegue la migrazione di risorse del gruppo di disponibilità a un nuovo cluster WSFC.  
  
 Per ulteriori informazioni, vedere [portare Offline di un gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/take-an-availability-group-offline-sql-server.md).  
  
## <a name="prerequisites-and-restrictions"></a>Prerequisiti e restrizioni  
 Per informazioni sui prerequisiti e restrizioni alle repliche di disponibilità e le istanze del server host e i computer, vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 Per informazioni sulle restrizioni sulle istruzioni AVAILABILITY GROUP Transact-SQL, vedere [Cenni preliminari su istruzioni Transact-SQL per gruppi di disponibilità AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/transact-sql-statements-for-always-on-availability-groups.md).  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  Richiede l'autorizzazione ALTER ANY DATABASE.   
  
## <a name="examples"></a>Esempi  
  
###  <a name="Join_Secondary_Replica"></a> A. Creazione di un join di una replica secondaria a un gruppo di disponibilità  
 Nell'esempio seguente viene creato un join di una replica secondaria a cui si è connessi al gruppo di disponibilità `AccountsAG`.  
  
```SQL  
ALTER AVAILABILITY GROUP AccountsAG JOIN;  
GO  
```  
  
###  <a name="Force_Failover"></a> B. Failover forzato di un gruppo di disponibilità  
 Nell'esempio seguente viene eseguito il failover forzato del gruppo di disponibilità `AccountsAG` alla replica secondaria a cui si è connessi.  
  
```SQL
ALTER AVAILABILITY GROUP AccountsAG FORCE_FAILOVER_ALLOW_DATA_LOSS;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREARE il gruppo di disponibilità &#40; Transact-SQL &#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [DROP AVAILABILITY GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/drop-availability-group-transact-sql.md)   
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Risolvere i problemi sempre sulla configurazione di gruppi di disponibilità &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)   
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Listener del gruppo di disponibilità, connettività Client e Failover dell'applicazione &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  
