---
title: "Gruppi di disponibilità distribuiti (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Availability Groups [SQL Server], distributed
ms.assetid: 
caps.latest.revision: 
author: allanhirt
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 245eb466e756017c3ae70a5fc408d4ce876370d4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="distributed-availability-groups"></a>Gruppi di disponibilità distribuiti
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] I gruppi di disponibilità distribuiti sono una nuova funzionalità introdotta in SQL Server 2016 come variante della funzionalità gruppi di disponibilità AlwaysOn esistente. Questo articolo illustra alcuni aspetti relativi ai gruppi di disponibilità distribuiti ed è complementare alla [documentazione di SQL Server](https://docs.microsoft.com/en-us/sql/sql-server/sql-server-technical-documentation) esistente.

> [!NOTE]
> "DAG" non è l'abbreviazione ufficiale del termine *gruppo di disponibilità distribuito*, perché tale abbreviazione è già usata per la funzionalità gruppo di disponibilità dei database di Exchange. La funzionalità di Exchange non ha alcuna relazione con i gruppi di disponibilità distribuiti o i gruppi di disponibilità di SQL Server.

Per configurare un gruppo di disponibilità distribuito, vedere [Configurare gruppi di disponibilità distribuiti](configure-distributed-availability-groups.md).

## <a name="understand-distributed-availability-groups"></a>Informazioni sui gruppi di disponibilità distribuiti

Un gruppo di disponibilità distribuito è un tipo particolare di gruppo di disponibilità che comprende due gruppi di disponibilità distinti. I gruppi di disponibilità sottostanti sono configurati in due diversi cluster di Windows Server Failover Clustering (WSFC). I gruppi di disponibilità che fanno parte di un gruppo di disponibilità distribuito non devono necessariamente trovarsi nella stessa posizione. Possono essere fisici, virtuali, in locale, nel cloud pubblico o in qualsiasi posizione supporti la distribuzione di un gruppo di disponibilità. Se due gruppi di disponibilità possono comunicare, è possibile usarli per configurare un gruppo di disponibilità distribuito.

Per un gruppo di disponibilità tradizionale, le risorse sono configurate in un cluster WSFC. Per un gruppo di disponibilità distribuito, nel cluster WSFC non viene configurato nulla. Tutti gli elementi che lo riguardano vengono mantenuti all'interno di SQL Server. Per sapere come visualizzare le informazioni relative a un gruppo di disponibilità distribuito, vedere [Visualizzare informazioni su un gruppo di disponibilità distribuito](#viewing-distributed-availability-group-information). 

Un gruppo di disponibilità distribuito richiede la presenza di un listener per i gruppi di disponibilità sottostanti. Anziché specificare il nome del server sottostante per un'istanza autonoma o, nel caso di un'istanza del cluster di failover di SQL Server, il valore associato alla risorsa del nome di rete, come si farebbe con un gruppo di disponibilità tradizionale, si specifica il listener configurato per il gruppo di disponibilità distribuito con il parametro ENDPOINT_URL durante la creazione. Anche se ogni gruppo di disponibilità sottostante del gruppo di disponibilità distribuito ha un listener, il gruppo di disponibilità distribuito non ha alcun listener.

La figura seguente mostra una panoramica generale di un gruppo di disponibilità distribuito che comprende due gruppi di disponibilità (AG 1 e AG 2), ognuno dei quali è configurato nel relativo cluster WSFC. Il gruppo di disponibilità distribuito ha un totale di quattro repliche, due in ogni gruppo di disponibilità. Ogni gruppo di disponibilità può supportare un numero massimo di repliche, perciò ogni gruppo di disponibilità può avere fino a 18 repliche.

<a name="fig1"></a>
![Panoramica generale di un gruppo di disponibilità distribuito][1]

È possibile configurare lo spostamento dei dati nei gruppi di disponibilità distribuiti come sincrono o asincrono. Tuttavia, lo spostamento dei dati all'interno di gruppi di disponibilità distribuiti è leggermente diverso rispetto a quanto avviene in un gruppo di disponibilità tradizionale. Anche se ogni gruppo di disponibilità ha una replica primaria, solo una copia dei database fa parte di un gruppo di disponibilità distribuito che può accettare inserimenti, aggiornamenti ed eliminazioni. Come illustra la figura seguente, AG 1 è il gruppo di disponibilità primario. La relativa replica primaria invia transazioni sia alle repliche secondarie di AG 1 che alla replica primaria di AG 2. La replica primaria di AG 2 è anche nota come *server di inoltro*. Un server di inoltro è una replica primaria in un gruppo di disponibilità secondario in un gruppo di disponibilità distribuito. Il server di inoltro riceve le transazioni dalla replica primaria nel gruppo di disponibilità primario e le inoltra alle repliche secondarie nel proprio gruppo di disponibilità.  Il server di inoltro mantiene quindi aggiornate le repliche secondarie di AG 2. 

![Gruppo di disponibilità distribuito e relativo spostamento dei dati][2]

L'unico modo per far sì che la replica primaria di AG 2 accetti inserimenti, aggiornamenti ed eliminazioni è effettuare manualmente il failover del gruppo di disponibilità distribuito da AG 1. Dato che AG 1, nella figura precedente, contiene la copia scrivibile del database, con un failover AG 2 diventa il gruppo di disponibilità che accetta inserimenti, aggiornamenti ed eliminazioni. Per informazioni su come effettuare il failover di un gruppo di disponibilità distribuito in un altro, vedere [Failover in un gruppo di disponibilità secondario]( https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups).

> [!NOTE]
> I gruppi di disponibilità distribuiti in SQL Server 2016 supportano il failover solo da un gruppo di disponibilità a un altro mediante l'opzione FORCE_FAILOVER_ALLOW_DATA_LOSS.

## <a name="sql-server-version-and-edition-requirements-for-distributed-availability-groups"></a>Requisiti di versione ed edizione di SQL Server per gruppi di disponibilità distribuiti

Attualmente i gruppi di disponibilità distribuiti funzionano solo con gruppi di disponibilità creati con la stessa versione principale di SQL Server. Ad esempio, attualmente tutti i gruppi di disponibilità che fanno parte di un gruppo di disponibilità distribuito devono essere creati con SQL Server 2016. Poiché la funzionalità gruppi di disponibilità distribuiti non esiste in SQL Server 2012 o SQL Server 2014, i gruppi di disponibilità creati con tali versioni non possono far parte di gruppi di disponibilità distribuiti. 

> [!NOTE]
> I gruppi di disponibilità distribuiti non possono essere configurati con la Standard Edition o una combinazione di Standard ed Enterprise Edition.

Vista la presenza di due gruppi di disponibilità separati, il processo di installazione di un Service Pack o di un aggiornamento cumulativo in una replica che fa parte di un gruppo di disponibilità distribuito è leggermente diverso da quanto avviene in un gruppo di disponibilità tradizionale:

1. Per iniziare, aggiornare le repliche del secondo gruppo di disponibilità nel gruppo di disponibilità distribuito.

2. Applicare patch alle repliche del gruppo di disponibilità primario nel gruppo di disponibilità distribuito.

3. Come per un gruppo di disponibilità standard, effettuare il failover del gruppo di disponibilità primario in una delle relative repliche, non nella replica primaria del secondo gruppo di disponibilità, e applicare le patch. Se l'unica replica presente è quella primaria, sarà necessario effettuare un failover manuale nel secondo gruppo di disponibilità.

> [!NOTE]
> Non sono stati pubblicati annunci sull'eventualità che nelle versioni future di SQL Server le versioni precedenti possano far parte dello stesso gruppo di disponibilità distribuito. In tal caso, sarebbe possibile includere i gruppi di disponibilità distribuiti in un piano di aggiornamento della versione di SQL Server.

### <a name="windows-server-versions-and-distributed-availability-groups"></a>Versioni e gruppi di disponibilità distribuiti di Windows Server

Un gruppo di disponibilità distribuito comprende più gruppi di disponibilità, ognuno nel relativo cluster WSFC sottostante, ed è un costrutto solo SQL Server.  Ciò significa che i cluster WSFC che ospitano i singoli gruppi di disponibilità possono avere versioni principali diverse di Windows Server. Le versioni principali di SQL Server devono essere uguali, come illustrato nella sezione precedente. Come la [figura iniziale](#fig1), la figura seguente mostra AG 1 e AG 2 come parte di un gruppo di disponibilità distribuito, ma ognuno dei cluster WSFC ha una versione diversa di Windows Server.


![Gruppi di disponibilità distribuiti con cluster WSFC con versioni diverse di Windows Server][3]

I singoli cluster WSFC e i relativi gruppi di disponibilità corrispondenti seguono regole tradizionali. Ciò significa che possono essere aggiunti a un dominio o non aggiunti a un dominio (Windows Server 2016 o versione successiva). Quando due gruppi di disponibilità diversi vengono combinati in un unico gruppo di disponibilità distribuito, gli scenari possibili sono quattro:

* Entrambi i cluster WSFC sono aggiunti allo stesso dominio.
* Ogni cluster WSFC è aggiunto a un dominio diverso.
* Un cluster WSFC è aggiunto a un dominio e l'altro cluster WSFC non è aggiunto a un dominio.
* Nessuno dei due cluster WSFC è aggiunto a un dominio.

Se entrambi i cluster WSFC sono aggiunti allo stesso dominio (non domini trusted), non è necessario eseguire operazioni particolari quando si crea il gruppo di disponibilità distribuito. Per gruppi di disponibilità e cluster WSFC non aggiunti allo stesso dominio, usare i certificati per consentire il funzionamento del gruppo di disponibilità distribuito, come per creare un gruppo di disponibilità per un gruppo di disponibilità indipendente dal dominio. Per informazioni su come configurare i certificati per un gruppo di disponibilità distribuito, seguire i passaggi da 3 a 13 della procedura illustrata in [Create a domain-independent availability group](domain-independent-availability-groups.md#create-a-domain-independent-availability-group) (Creare un gruppo di disponibilità indipendente dal dominio).

Con un gruppo di disponibilità distribuito, le repliche primarie in ogni gruppo di disponibilità sottostante devono avere i certificati delle altre repliche. Se sono già disponibili endpoint che non usano certificati, è possibile usare [ALTER ENDPOINT](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-endpoint-transact-sql) per riconfigurare gli endpoint in modo da riflettere l'uso dei certificati.

## <a name="distributed-availability-group-usage-scenarios"></a>Scenari di utilizzo di un gruppo di disponibilità distribuito

Di seguito sono riportati i tre scenari di utilizzo principali per un gruppo di disponibilità distribuito: 

* [Ripristino di emergenza e semplificazione delle configurazioni multisito](#disaster-recovery-and-multi-site-scenarios)
* [Migrazione a nuovo hardware oppure a nuove configurazioni, come ad esempio l'uso di nuovo hardware o la modifica di sistemi operativi sottostanti](#migration-using-a-distributed-availability-group)
* [Aumento del numero di repliche leggibili oltre otto in un singolo gruppo di disponibilità grazie all'estensione in più gruppi di disponibilità](#scaling-out-readable-replicas-with-distributed-accessibility-groups)

### <a name="disaster-recovery-and-multi-site-scenarios"></a>Scenari multisito e di ripristino di emergenza

In un gruppo di disponibilità tradizionale tutti i server devono far parte dello stesso cluster WSFC. Questo può rendere difficoltosa l'estensione in più data center. La figura seguente mostra l'aspetto dell'architettura di un gruppo di disponibilità multisito tradizionale, incluso il flusso di dati. Una replica primaria invia transazioni a tutte le repliche secondarie. Per alcuni versi, questa configurazione è meno flessibile di un gruppo di disponibilità distribuito. Ad esempio, è necessario implementare Active Directory (se applicabile) e il controllo del quorum nel cluster WSFC. Potrebbe anche essere necessario prendere in considerazione altri aspetti di un cluster WSFC, ad esempio la modifica dei voti del nodo.

![Gruppo di disponibilità multisito tradizionale][4]

I gruppi di disponibilità distribuiti offrono uno scenario di distribuzione più flessibile per i gruppi di disponibilità che comprendono più data center. È anche possibile usare i gruppi di disponibilità distribuiti dove in passato venivano usate funzionalità come il [log shipping]( https://docs.microsoft.com/en-us/sql/database-engine/log-shipping/about-log-shipping-sql-server). A differenza dei gruppi di disponibilità tradizionali, tuttavia, i gruppi di disponibilità distribuiti non possono avere un'applicazione ritardata delle transazioni. Ciò significa che i gruppi di disponibilità o i gruppi di disponibilità distribuiti non potranno essere utili in caso di errore umano in cui i dati vengano aggiornati o eliminati involontariamente.

I gruppi di disponibilità distribuiti sono a regime di controllo libero, vale a dire che in questo caso non richiedono un cluster WSFC singolo e vengono gestiti da SQL Server. Dato che i cluster WSFC vengono gestiti singolarmente e la sincronizzazione tra i due gruppi di disponibilità è principalmente asincrona, è più semplice configurare il ripristino di emergenza in un altro sito. Le repliche primarie in ogni gruppo di disponibilità sincronizzano le relative repliche secondarie.

* Un gruppo di disponibilità distribuito supporta unicamente il failover manuale. In una situazione di ripristino di emergenza in cui si vogliono cambiare i data center non è consigliabile configurare il failover automatico, tranne in rare eccezioni. 
* Probabilmente non sarà necessario impostare alcuni degli elementi o parametri tradizionali per i cluster o le subnet WSFC multisito, ad esempio CrossSubnetThreshold, ma sarà comunque necessario occuparsi della latenza di rete a un livello diverso per il trasporto dei dati. La differenza sta nel fatto che ogni cluster WSFC mantiene la relativa disponibilità. Il cluster non è un'unica grande entità composta da quattro nodi. Sono presenti due cluster WSFC sperati di due nodi, come illustra la figura precedente.  
* È consigliabile adottare l'approccio con spostamento dei dati asincrono, perché è il più adatto ai fini del ripristino di emergenza.
* Se si configura lo spostamento dei dati sincrono tra la replica primaria e almeno una replica secondaria del secondo gruppo di disponibilità e si configura lo spostamento sincrono nel gruppo di disponibilità distribuito, un gruppo di disponibilità distribuito dovrà attendere la conferma della ricezione dei dati da tutte le copie sincrone.

### <a name="migrate-by-using-a-distributed-availability-group"></a>Eseguire la migrazione con un gruppo di disponibilità distribuito

I gruppi di disponibilità distribuiti supportano due configurazioni dei gruppi di disponibilità completamente diverse e semplificano non soltanto gli scenari di ripristino di emergenza e multisito, ma anche gli scenari di migrazione. Se si esegue la migrazione in un nuovo hardware o in macchine virtuali, locali o IaaS nel cloud pubblico, la configurazione di un gruppo di disponibilità distribuito consente di usare la migrazione in situazioni in cui, in passato, era necessario usare il backup, la copia, il ripristino o il log shipping. 

La possibilità di eseguire la migrazione è particolarmente utile negli scenari in cui si modifica o si aggiorna il sistema operativo sottostante, mantenendo però la stessa versione di SQL Server. Anche se Windows Server 2016 consente l'aggiornamento in sequenza da Windows Server 2012 R2 nello stesso hardware, la maggior parte degli utenti sceglie di eseguire la distribuzione di nuovo hardware o macchine virtuali. 

Per completare la migrazione alla nuova configurazione, alla fine del processo, arrestare tutto il traffico dei dati verso il gruppo di disponibilità originale e configurare il gruppo di disponibilità distribuito per lo spostamento dei dati sincrono. Questa operazione fa in modo che la replica primaria del secondo gruppo di disponibilità sia completamente sincronizzata ed elimina il rischio di perdita di dati. Dopo aver verificato la sincronizzazione, effettuare il failover del gruppo di disponibilità distribuito nel gruppo di disponibilità secondario. Per altre informazioni, vedere [Failover su un gruppo di disponibilità secondario](configure-distributed-availability-groups.md#failover).

Dopo la migrazione, il secondo gruppo di disponibilità è ora il nuovo gruppo di disponibilità primario e potrebbe essere necessario eseguire una di queste operazioni:

* Rinominare il listener nel gruppo di disponibilità secondario e, possibilmente, eliminare o rinominare quello precedente nel gruppo di disponibilità primario originale oppure ricrearlo usando il listener del gruppo di disponibilità primario originale, in modo che le applicazioni e gli utenti possano accedere alla nuova configurazione.
* Se non è possibile rinominarlo o ricrearlo, indirizzare applicazioni e utenti al listener nel secondo gruppo di disponibilità.

### <a name="scale-out-readable-replicas-with-distributed-availability-groups"></a>Aumentare le istanze di repliche leggibili con gruppi di disponibilità distribuiti

Un singolo gruppo di disponibilità distribuito può avere fino a 16 repliche secondarie, in base alle esigenze. Può quindi avere fino a 18 copie per la lettura, incluse le due repliche primarie dei diversi gruppi di disponibilità. Ciò significa che più di un sito può avere accesso in tempo quasi reale per l'invio di segnalazioni a varie applicazioni.

I gruppi di disponibilità distribuiti consentono un maggiore aumento delle istanze di una farm di sola lettura rispetto a quanto avviene con un gruppo di disponibilità singolo. Per aumentare le istanze di repliche leggibili con un gruppo di disponibilità distribuito, è possibile procedere in due modi:

* È possibile usare la replica primaria del secondo gruppo di disponibilità in un gruppo di disponibilità distribuito per creare un altro gruppo di disponibilità distribuito, anche se il database non è in RECOVERY.
* È anche possibile usare la replica primaria del primo gruppo di disponibilità per creare un altro gruppo di disponibilità distribuito.

In altre parole, una replica primaria può far parte di due diversi gruppi di disponibilità distribuiti. La figura seguente mostra che AG 1 e AG 2 fanno parte di Distributed AG 1, mentre AG 2 e AG 3 fanno parte di Distributed AG 2. La replica primaria (o server di inoltro) di AG 2 è una replica secondaria per Distributed AG 1, ma è anche una replica primaria per Distributed AG 2.

![Aumento delle istanze di lettura con gruppi di disponibilità distribuiti][5]

La figura seguente mostra AG 1 come replica primaria per due gruppi di disponibilità distribuiti diversi: Distributed AG 1, composto da AG 1 e AG 2, e Distributed AG 2, composto da AG 1 e AG 3.


![Altro esempio di aumento delle istanze di lettura con gruppi di disponibilità distribuiti][6]


In entrambi gli esempi precedenti si possono avere fino a 27 repliche totali tra i tre gruppi di disponibilità, ognuno dei quali può essere usato per query di sola lettura. 

Il [routing di sola lettura]( https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server) attualmente non funziona con i gruppi di disponibilità distribuiti. Tutte le query che usano il listener per connettersi vanno alla replica primaria. In caso contrario, è necessario configurare ogni replica in modo da consentire tutte le connessioni come replica secondaria e accedervi direttamente. Questo comportamento potrà essere modificato in un aggiornamento di SQL Server 2016 o in una versione futura di SQL Server.

## <a name="initialize-secondary-availability-groups-in-a-distributed-availability-group"></a>Inizializzare gruppi di disponibilità secondari in un gruppo di disponibilità distribuito

I gruppi di disponibilità distribuiti usano il [seeding automatico]( https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group) come metodo principale per inizializzare la replica primaria nel secondo gruppo di disponibilità. Perché sia possibile un ripristino completo del database nella replica primaria del secondo gruppo di disponibilità, seguire questa procedura:

1. Ripristinare il backup del database WITH NORECOVERY.
2. Se necessario, ripristinare i backup del log delle transazioni WITH NORECOVERY appropriato.
3. Creare il secondo gruppo di disponibilità senza specificare un nome di database e con SEEDING_MODE impostato su AUTOMATIC.
4. Creare il gruppo di disponibilità distribuito usando il seeding automatico.

Quando si aggiunge la replica primaria del secondo gruppo di disponibilità al gruppo di disponibilità distribuito, la replica viene confrontata con i database primari del primo gruppo di disponibilità e il seeding rileva il database fino all'origine. Tenere presente alcune considerazioni:

* L'output visualizzato in `sys.dm_hadr_automatic_seeding`, nella replica primaria del secondo gruppo di disponibilità, avrà `current_state` impostato su FAILED con il motivo "Seeding Check Message Timeout" (Timeout messaggio di controllo seeding).

* Il log di SQL Server corrente nella replica primaria del secondo gruppo di disponibilità mostrerà che il seeding ha avuto esito positivo e che gli [LSN]( https://docs.microsoft.com/en-us/sql/relational-databases/sql-server-transaction-log-architecture-and-management-guide) sono stati sincronizzati.

* L'output visualizzato in `sys.dm_hadr_automatic_seeding`, nella replica primaria del primo gruppo di disponibilità, avrà current_state impostato su COMPLETED. 

* Il seeding ha anche un comportamento diverso con i gruppi di disponibilità distribuiti. Perché il seeding possa iniziare nella seconda replica, è necessario eseguire il comando `ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE` nella replica. Anche se questa condizione è vera per tutte le repliche secondarie che fanno parte del gruppo di disponibilità sottostante, la replica primaria del secondo gruppo di disponibilità ha già le autorizzazioni appropriate per consentire l'avvio del seeding dopo l'aggiunta al gruppo di disponibilità distribuito. 

### <a name="view-distributed-availability-group-information"></a>Visualizzare informazioni su un gruppo di disponibilità distribuito 
    
Come accennato in precedenza, un gruppo di disponibilità distribuito è un costrutto solo SQL Server e non viene visualizzato nel cluster WSFC sottostante. La figura seguente mostra due diversi cluster WSFC (CLUSTER_A e CLUSTER_B), ognuno con i relativi gruppi di disponibilità. Qui vengono illustrati solo AG1 in CLUSTER_A e AG2 in CLUSTER_B. 

<!-- ![Two WSFC clusters with multiple availability groups through PowerShell Get-ClusterGroup command][7]  -->
<a name="fig7"></a>

```
PS C:\> Get-ClusterGroup -Cluster CLUSTER_A

Name                            OwnerNode             State
----                            ---------             -----
AG1                             DENNIS                Online
Available Storage               GLEN                  Offline
Cluster Group                   JY                    Online
New_RoR                         DENNIS                Online
Old_RoR                         DENNIS                Online
SeedingAG                       DENNIS                Online


PS C:\> Get-ClusterGroup -Cluster CLUSTER_B

Name                            OwnerNode             State
----                            ---------             -----
AG2                             TOMMY                 Online
Available Storage               JC                    Offline
Cluster Group                   JC                    Online
```

Tutte le informazioni dettagliate su un gruppo di disponibilità distribuito sono disponibili in SQL Server, in particolare nelle viste a gestione dinamica del gruppo di disponibilità. Le uniche informazioni attualmente visualizzate in SQL Server Management Studio per un gruppo di disponibilità distribuito sono disponibili nella replica primaria per i gruppi di disponibilità. Come mostrato nella figura seguente, nella cartella Gruppi di disponibilità di SQL Server Management Studio è disponibile un gruppo di disponibilità distribuito. La figura mostra AG1 come replica primaria per un singolo gruppo di disponibilità locale per tale istanza, non per un gruppo di disponibilità distribuito.

![Visualizzazione in SQL Server Management Studio della replica primaria sul primo cluster WSFC di un gruppo di disponibilità distribuito][8]


Se tuttavia si fa clic con il pulsante destro del mouse sul gruppo di disponibilità distribuito, non sono disponibili opzioni (vedere la figura seguente) e le cartelle Database di disponibilità, Listener gruppo di disponibilità e Repliche di disponibilità espanse sono tutte vuote. SQL Server Management Studio 16 mostra questo risultato, ma è possibile che tale comportamento venga modificato in una versione futura di SQL Server Management Studio.

![Nessuna opzione disponibile per l'azione][9]

Come mostrato nella figura seguente, le repliche secondarie non mostrano alcun valore in SQL Server Management Studio correlato al gruppo di disponibilità distribuito. I nomi di questi gruppi di disponibilità sono mappati ai ruoli mostrati nell'immagine precedente del [cluster CLUSTER_A WSFC](#fig7).

![Visualizzazione di una replica secondaria in SQL Server Management Studio][10]

Gli stessi concetti sono validi quando si usano le viste a gestione dinamica. Usando la query seguente è possibile visualizzare tutti i gruppi di disponibilità (normali e distribuiti) e i rispettivi nodi. Questo risultato viene visualizzato solo se si esegue una query sulla replica primaria in uno dei cluster WSFC inclusi nel gruppo di disponibilità distribuito. Nella vista a gestione dinamica `sys.availability_groups` è disponibile una nuova colonna denominata `is_distributed`, che corrisponde a 1 quando il gruppo di disponibilità è un gruppo di disponibilità distribuito. Per visualizzare questa colonna:

```sql
SELECT ag.[name] as 'AG Name', 
    ag.Is_Distributed, 
    ar.replica_server_name as 'Replica Name'
FROM    sys.availability_groups ag, 
    sys.availability_replicas ar       
WHERE   ag.group_id = ar.group_id
```

Un esempio di output dal secondo cluster WSFC incluso in un gruppo di disponibilità distribuito viene mostrato nella figura seguente. SPAG1 è costituito da due repliche: DENNIS e JY. Il gruppo di disponibilità distribuito denominato SPDistAG include tuttavia i nomi dei due gruppi di disponibilità inclusi (SPAG1 e SPAG2), invece dei nomi delle istanze, usati in un gruppo di disponibilità tradizionale. 

![Output di esempio della query precedente][11]

In SQL Server Management Studio qualsiasi stato mostrato nel Dashboard e in altre aree è relativo solo alla sincronizzazione locale entro tale gruppo di disponibilità. Per visualizzare l'integrità di un gruppo di disponibilità distribuito, eseguire query nelle viste a gestione dinamica. La query di esempio seguente estende e perfeziona la query precedente:

```sql
SELECT ag.[name] as 'AG Name', ag.is_distributed, ar.replica_server_name as 'Underlying AG', ars.role_desc as 'Role', ars.synchronization_health_desc as 'Sync Status'
FROM    sys.availability_groups ag, 
sys.availability_replicas ar,       
sys.dm_hadr_availability_replica_states ars       
WHERE   ar.replica_id = ars.replica_id
and     ag.group_id = ar.group_id 
and ag.is_distributed = 1
```
       
       
![Stato del gruppo di disponibilità distribuito][12]


Per estendere ulteriormente la query precedente, è anche possibile visualizzare le prestazioni sottostanti tramite le viste a gestione dinamica aggiungendo `sys.dm_hadr_database_replicas_states`. La vista a gestione dinamica archivia attualmente informazioni solo sul secondo gruppo di disponibilità. La query di esempio seguente, eseguita sul gruppo di disponibilità primario, produce l'output di esempio mostrato di seguito:

```
SELECT ag.[name] as 'Distributed AG Name', ar.replica_server_name as 'Underlying AG', dbs.[name] as 'DB', ars.role_desc as 'Role', drs.synchronization_health_desc as 'Sync Status', drs.log_send_queue_size, drs.log_send_rate, drs.redo_queue_size, drs.redo_rate
FROM    sys.databases dbs,
    sys.availability_groups ag,
    sys.availability_replicas ar,
    sys.dm_hadr_availability_replica_states ars,
    sys.dm_hadr_database_replica_states drs
WHERE   drs.group_id = ag.group_id
and ar.replica_id = ars.replica_id
and ars.replica_id = drs.replica_id
and dbs.database_id = drs.database_id
and ag.is_distributed = 1
```

![Informazioni sulle prestazioni per un gruppo di disponibilità distribuito][13]


### <a name="next-steps"></a>Passaggi successivi 

* [Usare la Creazione guidata Gruppo di disponibilità (SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)

* [Usare la finestra di dialogo Nuovo gruppo di disponibilità (SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)
 
* [Creare un gruppo di disponibilità con Transact-SQL](create-an-availability-group-transact-sql.md)

<!--Image references-->
[1]: ./media/dag-01-high-level-view-distributed-ag.png
[2]: ./media/dag-02-distributed-ag-data-movement.png
[3]: ./media/dag-03-distributed-ags-wsfcs-different-versions-windows-server.png
[4]: ./media/dag-04-traditional-multi-site-ag.png
[5]: ./media/dag-05-scaling-out-reads-with-distributed-ags.png
[6]: ./media/dag-06-another-scaling-out-reads-using-distributed-ags-example.png
[7]: ./media/dag-07-two-wsfcs-multiple-ags-through-get-clustergroup-command.png
[8]: ./media/dag-08-view-smss-primary-replica-first-wsfc-distributed-ag.png
[9]: ./media/dag-09-no-options-available-action.png
[10]: ./media/dag-10-view-ssms-secondary-replica.png
[11]: ./media/dag-11-example-output-of-query-above.png
[12]: ./media/dag-12-distributed-ag-status.png
[13]: ./media/dag-13-performance-information-distributed-ag.png

 
