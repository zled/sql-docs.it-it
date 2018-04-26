---
title: Gruppi di disponibilità per SQL Server in Linux Always On | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.workload: On Demand
ms.openlocfilehash: 9d442c41adaec7148b3eb0259f851fee3fd2b683
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="always-on-availability-groups-on-linux"></a>Gruppi di disponibilità in Linux Always On

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo descrive le caratteristiche di gruppi di disponibilità AlwaysOn (estensivi) in basati su Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] installazioni. Vengono inoltre illustrate le differenze tra il cluster di failover di Windows Server (WSFC) e Linux-base estensivi. Vedere il [documentazione basati su Windows](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) per le nozioni di base di estensivi, come funzionano nello stesso modo in Windows e Linux, ad eccezione di WSFC.

Dal punto di vista di alto livello, dei gruppi di disponibilità in [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in Linux sono uguali a quelli nelle implementazioni basata su WSFC. Ciò significa che tutte le limitazioni e le funzionalità sono gli stessi, con alcune eccezioni. Le differenze principali includono:

-   Microsoft Distributed Transaction Coordinator (DTC) non è supportata in Linux in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Se le applicazioni richiedono l'uso di transazioni distribuite e un gruppo di disponibilità, distribuire [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in Windows.
-   Le distribuzioni basate su Linux usare Pacemaker invece di un cluster WSFC.
-   La maggior parte delle configurazioni per estensivi in Windows, ad eccezione dello scenario di Cluster del gruppo di lavoro, a differenza di Pacemaker non richiede mai servizi di dominio Active Directory (AD DS).
-   Come eseguire un gruppo di disponibilità da un nodo a un altro è diversa tra Linux e Windows.
-   Alcune impostazioni, ad esempio `required_synchronized_secondaries_to_commit` possono essere modificate solo tramite Pacemaker su Linux, mentre un'installazione basata su WSFC utilizza Transact-SQL.

## <a name="number-of-replicas-and-cluster-nodes"></a>Numero di repliche e i nodi del cluster

Un gruppo di disponibilità in [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)] può avere due repliche totale: uno primario e uno secondario che può essere utilizzato solo per scopi di disponibilità. E non può essere utilizzato per altri scopi, ad esempio le query leggibile. Un gruppo di disponibilità in [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)] può avere fino a nove repliche totale: una primaria e fino a otto repliche secondarie, dei quali fino a tre (incluso il primario) può essere sincrona. Se si utilizza un cluster sottostante, può esistere un massimo di 16 nodi totale quando è coinvolto Corosync. Un gruppo di disponibilità può estendersi al massimo nove di 16 nodi con [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]e due con [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)].

Una configurazione di due repliche che richiede la possibilità di eseguire automaticamente il failover a un'altra replica richiede l'utilizzo di una configurazione replica sola, come descritto in [quorum e configurazione di replica di sola](#configuration-only-replica-and-quorum). Le repliche di configurazione sono state introdotte in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] aggiornamento cumulativo 1 (CU1), in modo che deve essere la versione minima di distribuzione per questa configurazione.

Se viene utilizzato il Pacemaker, deve essere configurata correttamente in modo che rimanga in esecuzione. Ciò significa che quorum e STONITH deve essere implementato correttamente da una prospettiva Pacemaker, oltre a qualsiasi [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] requisiti, ad esempio una sola configurazione di replica.

Repliche secondarie leggibili sono supportate solo con [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)].

## <a name="cluster-type-and-failover-mode"></a>Modalità di tipo e il failover del cluster

Novità di [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] è l'introduzione di un tipo di cluster per estensivi. Per Linux, sono disponibili due valori validi: esterno e nessuno. Un tipo di cluster di esterni significa Pacemaker verrà utilizzato di sotto del gruppo di disponibilità. Utilizzo esterno per il tipo di cluster, è necessario impostare la modalità di failover su esterno anche (nuova [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]). Failover automatico è supportato, ma a differenza di un cluster WSFC, la modalità di failover è impostata su esterno, non è automatica, quando viene utilizzato il Pacemaker. A differenza di un cluster WSFC, la parte Pacemaker del gruppo di disponibilità viene creata dopo aver configurato il gruppo di disponibilità.

Un tipo di cluster None indica che non c'è Nessun requisito per né verrà utilizzato il gruppo di disponibilità, Pacemaker. Anche nei server che dispongono di Pacemaker configurato, se un gruppo di disponibilità è configurato con un tipo di cluster None, Pacemaker verrà non visualizzare o gestire tale gruppo di disponibilità. Un tipo di cluster None supporta solo il failover manuale da un database primario a una replica secondaria. Un gruppo di disponibilità creato con nessuno è destinata principalmente per la lettura con scalabilità orizzontale scenario, nonché gli aggiornamenti. Anche se può funzionare in scenari di ripristino di emergenza o di disponibilità locale in cui è necessario alcun failover automatico, non è consigliabile. La sequenza di listener è inoltre più complessa senza Pacemaker.

Tipo di cluster è archiviato nel [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] vista a gestione dinamica (DMV) `sys.availability_groups`, nelle colonne `cluster_type` e `cluster_type_desc`.

## <a name="requiredsynchronizedsecondariestocommit"></a>obbligatorio\_sincronizzato\_secondari\_a\_commit

Novità di [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] è un'impostazione che viene utilizzata da estensivi chiamati `required_synchronized_secondaries_to_commit`. In questo modo il gruppo di disponibilità il numero di repliche secondarie che deve essere in contemporanea con la replica primaria. Ciò consente ad esempio il failover automatico (solo quando è integrato con Pacemaker con un tipo di cluster di esterni) e controlla il comportamento delle operazioni come la disponibilità del database primario, se il numero di repliche secondarie è online oppure offline. Per comprendere meglio il funzionamento, vedere [elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](sql-server-linux-availability-group-ha.md). Il `required_synchronized_secondaries_to_commit` valore è impostato per impostazione predefinita e gestita da Pacemaker /[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. È possibile eseguire manualmente l'override di questo valore.

La combinazione di `required_synchronized_secondaries_to_commit` e il nuovo numero di sequenza (che viene archiviato `sys.availability_groups`) informa Pacemaker e [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] che, ad esempio, può verificarsi il failover automatico. In tal caso, una replica secondaria avrebbe lo stesso numero di sequenza del database primario, vale a dire aggiornato con tutte le informazioni di configurazione più recente.

Sono disponibili tre valori che possono essere impostati per `required_synchronized_secondaries_to_commit`: 0, 1 o 2. Controllano il comportamento di ciò che accade quando una replica diventa non disponibile. I numeri corrispondono al numero di repliche secondarie che devono essere sincronizzati con la replica primaria. Il comportamento è come indicato di seguito in Linux:

-   0 – il failover automatico non è possibile perché nessuna replica secondaria deve essere sincronizzato. Il database primario è disponibile in qualsiasi momento.
-   Da 1 a una replica secondaria deve essere in uno stato sincronizzato con la replica primaria; failover automatico è possibile. Il database primario non è disponibile fino a quando non è disponibile una replica secondaria sincrona.
-   2 – sia nelle repliche secondarie in una configurazione di gruppo di disponibilità tre o più nodi deve essere sincronizzati con la replica primaria; failover automatico è possibile.

`required_synchronized_secondaries_to_commit` Controlla non solo il comportamento di failover con repliche sincrone, ma la perdita di dati. Con un valore pari a 1 o 2, una replica secondaria deve sempre essere sincronizzati, pertanto sarà sempre presente la ridondanza dei dati. Ciò non significa che perdita di dati.

Per modificare il valore di `required_synchronized_secondaries_to_commit`, utilizzare la sintassi seguente:

>[!NOTE]
>La modifica del valore determina la risorsa per il riavvio vale a dire brevi interruzioni. L'unico modo per evitare questo problema consiste nell'impostare la risorsa a non essere gestito dal cluster temporaneamente.

**Red Hat Enterprise Linux (RHEL) e Ubuntu**

```bash
sudo pcs resource update <AGResourceName> required_synchronized_secondaries_to_commit=<Value>
```

**SUSE Linux Enterprise Server (SLES)**

```bash
sudo crm resource param ms-<AGResourceName> set required_synchronized_secondaries_to_commit <value>
```

dove *AGResourceName* è il nome della risorsa configurata per il gruppo di disponibilità e *valore* è 0, 1 o 2. Per impostare nuovamente il valore predefinito di gestione il parametro Pacemaker, eseguire la stessa istruzione non prevede alcun valore.

Failover automatico di un gruppo di disponibilità è possibile quando vengono soddisfatte le condizioni seguenti:

-   Il database primario e la replica secondaria vengono impostate per lo spostamento di dati sincroni.
-   Il database secondario ha uno stato di sincronizzazione (non in sincronizzazione), ovvero che i due sono nello stesso punto dati.
-   Il tipo di cluster è impostato su esterno. Failover automatico non è possibile con un tipo di cluster None.
-   Il `sequence_number` della replica secondaria che diventerà il database primario è il numero di sequenza più alto: in altre parole, la replica secondaria `sequence_number` corrisponda a quella dalla replica primaria originale.

Se queste condizioni vengono soddisfatte e il server che ospita la replica primaria non riesce, il gruppo di disponibilità passerà proprietà a una replica sincrona. Il comportamento per le repliche sincrone (di cui è possibile tre totale: uno primario e due repliche secondarie) può essere controllata ulteriormente da `required_synchronized_secondaries_to_commit`. Funziona con estensivi su Windows e Linux, ma è configurato in modo completamente diverso. In Linux, il valore viene configurato automaticamente dal cluster della risorsa gruppo di disponibilità se stesso.

## <a name="configuration-only-replica-and-quorum"></a>Quorum e configurazione di replica di sola

Nuova [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] a partire da CU1 è una sola configurazione di replica. Poiché Pacemaker è diverso rispetto a un cluster WSFC, soprattutto quando si tratta di quorum e STONITH, richiedere una configurazione di due nodi non funzionerà quando si tratta di un gruppo di disponibilità. Per un'istanza FCI, i meccanismi di quorum forniti da Pacemaker possono costituire un problema, poiché l'arbitraggio di failover tutte le istanza cluster di failover si verifica a livello del cluster. Per un gruppo di disponibilità, arbitraggio in Linux avviene [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], in cui vengono archiviati tutti i metadati. Si tratta in cui la replica solo configurazione entra in gioco.

Senza altri elementi, un terzo nodo e almeno una replica sincronizzata sarebbe necessari. Questo metodo non funziona per [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)], dal momento che può avere solo due repliche che partecipano a un gruppo di disponibilità. La replica solo configurazione memorizza la configurazione del gruppo di disponibilità nel database master, come le altre repliche nella configurazione del gruppo di disponibilità. La sola configurazione di replica non dispone dei database utente che fanno parte del gruppo di disponibilità. I dati di configurazione viene inviati in modo sincrono dal database primario. Questi dati di configurazione viene quindi utilizzati durante i failover, sia automatico o manuale.

Per un gruppo di disponibilità mantenere il quorum e abilitare i failover automatici con un tipo di cluster di esterni, uno deve essere:

-   Avere tre repliche sincrone ([!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)] solo); o
-   Disporre di due repliche (primaria e secondaria), nonché una replica di sola configurazione.

I failover manuali possono verificarsi se l'utilizzo esterno o nessuno tipi per le configurazioni del gruppo di disponibilità del cluster. Mentre una sola configurazione di replica può essere configurata con un gruppo di disponibilità che dispone di un cluster di tipo None, non è consigliabile, poiché complica la distribuzione. Per tali configurazioni, modificare manualmente `required_synchronized_secondaries_to_commit` per avere un valore di almeno 1, in modo che sia presente almeno una replica sincronizzata.

Una configurazione replica sola può essere ospitata in qualsiasi edizione di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], tra cui [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]. Questo riduce al minimo i costi di licenza e assicura il funzionamento con estensivi in [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]. Ciò significa che il terzo necessari server sufficiente soddisfare i requisiti minimi per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], dal momento che per il gruppo di disponibilità non riceve traffico transazione utente.

Quando viene utilizzata una sola configurazione di replica, ha il comportamento seguente:

-   Per impostazione predefinita, `required_synchronized_secondaries_to_commit` è impostato su 0. Questo può essere modificato manualmente su 1 se si desidera.
-   Se il database primario non riesce e `required_synchronized_secondaries_to_commit` è 0, la replica secondaria diventeranno nel nuovo database primario e disponibile per la lettura e scrittura. Se il valore è 1, si verificherà il failover automatico, ma non verrà accettate nuove transazioni fino a quando non è in linea di altra replica.
-   Se ha esito negativo di una replica secondaria e `required_synchronized_secondaries_to_commit` è 0, la replica primaria è ancora accetta le transazioni, ma se il database primario non riesce a questo punto, non è presente alcuna protezione dati per i dati né di failover possibili (manuale o automatico), poiché una replica secondaria non è disponibile.
-   Se le repliche di sola configurazione non riesce, il gruppo di disponibilità funzionerà normalmente ma il failover automatico non è possibile.
-   Se una replica secondaria asincrona sia la replica solo configurazione non riesce, il database primario non può accettare transazioni, e non avere esito negativo per la replica primaria.

In CU1 nel è presente un bug noto la registrazione nel file che viene generato tramite corosync.log `mssql-server-ha`. Se una replica secondaria non è in grado di diventare il database primario a causa del numero di repliche obbligatorie disponibile, viene visualizzato il messaggio corrente "destinati a ricevere i numeri di sequenza 1 ma ricevuti solo 2. Non sono sufficienti le repliche sono in linea per alzare di livello in modo sicuro la replica locale." I numeri devono essere annullati e dovrebbe essere visualizzato "destinati a ricevere i numeri di sequenza 2 ma ricevuti solo 1. Non sono sufficienti le repliche sono in linea per alzare di livello in modo sicuro la replica locale." 

## <a name="multiple-availability-groups"></a>Più gruppi di disponibilità 

È possibile creare più di un gruppo di disponibilità per ogni cluster Pacemaker o set di server. L'unica limitazione consiste le risorse di sistema. Proprietà del gruppo di disponibilità viene visualizzata per lo schema. Possono essere di proprietà estensivi diversi da nodi diversi; non tutte devono essere in esecuzione nello stesso nodo.

## <a name="drive-and-folder-location-for-databases"></a>Percorso di unità e la cartella per i database

Come in estensivi basati su Windows, la struttura di unità e la cartella per i database utente che fanno parte di un gruppo di disponibilità deve essere identica. Ad esempio, se i database utente sono in `/var/opt/mssql/userdata` sul Server A, tale cartella stessa deve esistere nel Server B. L'unica eccezione è indicato nella sezione [interoperabilità con i gruppi di disponibilità basato su Windows e le repliche](#interoperability-with-windows-based-availability-groups-and-replicas).

## <a name="the-listener-under-linux"></a>Il listener in Linux

Il listener è una funzionalità facoltativa per un gruppo di disponibilità. Fornisce un singolo punto di ingresso per tutte le connessioni (lettura/scrittura per la replica primaria e/o le repliche di sola lettura al database secondario) in modo che le applicazioni e gli utenti finali non è necessario conoscere il server che ospita i dati. In un cluster WSFC, è la combinazione di una risorsa nome di rete e una risorsa IP, che viene quindi registrata nel dominio di Active Directory (se necessario) e DNS. In combinazione con la risorsa del gruppo di disponibilità se stesso, fornisce tale astrazione. Per ulteriori informazioni su un listener, vedere [listener, connettività Client e Failover dell'applicazione](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md).

Il listener in Linux è configurato in modo diverso, ma la relativa funzionalità è lo stesso. Non è previsto di una risorsa nome di rete in Pacemaker, né viene creato un oggetto in Active Directory; è solo una risorsa di indirizzo IP creata in Pacemaker eseguibili su uno dei nodi. È necessario creare una voce associata alla risorsa IP per il listener in DNS con un "nome descrittivo". La risorsa IP per il listener solo sarà attiva nel server che ospita la replica primaria per tale gruppo di disponibilità.

Se viene utilizzato il Pacemaker e viene creata una risorsa indirizzo IP che è associato il listener, esisterà brevi interruzioni come l'indirizzo IP si arresta in un server e viene avviata da altro, se si tratta di failover automatico o manuale. Sebbene offra astrazione tramite la combinazione di un solo nome e indirizzo IP, non maschera l'interruzione. Un'applicazione deve essere in grado di gestire la disconnessione con un tipo di funzionalità rileva il problema e riconnettersi.

Tuttavia, la combinazione del nome DNS e indirizzo IP è ancora non è sufficiente per fornire tutte le funzionalità che fornisce un listener su un cluster WSFC, ad esempio di routing di sola lettura per le repliche secondarie. Quando si configura un gruppo di disponibilità, un "listener" ancora deve essere configurato [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Può essere considerato la procedura guidata, nonché la sintassi Transact-SQL. Esistono due modi, che può essere configurato per funzionare anche in Windows:

-   Per un gruppo di disponibilità con un tipo di cluster di esterni, l'indirizzo IP associato l'oggetto creato in "listener" [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] deve essere l'indirizzo IP della risorsa creata in Pacemaker.
-   Per un gruppo di disponibilità creato con un tipo di cluster None, utilizzare l'indirizzo IP associato con la replica primaria.

L'istanza associata quindi l'indirizzo IP specificato diventa il coordinatore per elementi come le richieste di routine di sola lettura dalle applicazioni.

## <a name="interoperability-with-windows-based-availability-groups-and-replicas"></a>Interoperabilità con i gruppi di disponibilità basato su Windows e repliche 

Un gruppo di disponibilità di un cluster di tipo esterno o di un WSFC non può avere le relative repliche tra piattaforme. È true se il gruppo di disponibilità è [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)] o [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]. Ciò significa che in una configurazione gruppo di disponibilità tradizionali con un cluster sottostante, una replica non può essere in un cluster WSFC e l'altro in Linux con Pacemaker.

Un gruppo di disponibilità con un tipo di cluster None può avere le relative repliche tra i limiti del sistema operativo, in modo stesso AG possono essere entrambe le repliche basate su Linux e Windows. Come illustrato di seguito in cui la replica primaria è basato su Windows, mentre il database secondario è su una delle distribuzioni di Linux.

![Ibrida nessuno](./media/sql-server-linux-availability-group-overview/image1.png)

Un gruppo di disponibilità distribuita anche può attraversare i limiti del sistema operativo. Gli estensivi sottostante associati dalle regole per la relativa configurazione, ad esempio quello configurato con l'esterno da Linux sola, ma il gruppo di disponibilità unita in join a potrebbe essere configurato utilizzando un cluster WSFC. Si consideri l'esempio descritto di seguito.

![Gruppo di disponibilità Dist ibrida](./media/sql-server-linux-availability-group-overview/image2.png)

<!-- Distributed AGs are also supported for upgrades from [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] to [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. For more information on how to achieve this, see [the article “x”].

If using automatic seeding with a distributed availability group that crosses OSes, it can handle the differences in folder structure. How this works is described in [the documentation for automatic seeding].
-->
 
## <a name="next-steps"></a>Passaggi successivi
[Configurare il gruppo di disponibilità per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md)

[Configurare il gruppo di disponibilità a livello di lettura per SQL Server in Linux](sql-server-linux-availability-group-configure-rs.md)

[Aggiungere il gruppo di disponibilità risorse Cluster su RHEL](sql-server-linux-availability-group-cluster-rhel.md)

[Aggiungere il gruppo di disponibilità risorsa Cluster in SLES](sql-server-linux-availability-group-cluster-sles.md)

[Aggiungere il gruppo di disponibilità risorsa Cluster in Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

[Configurare un gruppo di disponibilità multipiattaforma](sql-server-linux-availability-group-cross-platform.md)

