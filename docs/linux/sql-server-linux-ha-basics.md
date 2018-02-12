---
title: "Nozioni fondamentali sulla disponibilità di SQL Server per le distribuzioni di Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: d53e54c6e8e74970316de557ddf3bd60a09e9ffe
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>Nozioni fondamentali sulla disponibilità di SQL Server per le distribuzioni di Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

A partire da [!INCLUDE[sssql17-md](../includes/sssql17-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] è supportato in Linux e Windows. Ad esempio basato su Windows [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] le distribuzioni, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] istanze e database è necessario essere a disponibilità elevata in Linux. In questo articolo vengono illustrati gli aspetti tecnici di pianificazione e distribuzione a disponibilità elevata basate su Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] database e istanze, nonché alcune delle differenze di installazioni basate su Windows. Poiché [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] potrebbero essere nuovi per professionisti IT di Linux e Linux potrebbero essere nuovi per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] professionisti, l'articolo a volte vengono introdotti i concetti che possono essere familiare ad alcune e non si ha dimestichezza ad altri utenti.

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]opzioni di disponibilità per le distribuzioni di Linux
Oltre a backup e ripristino, le stesse funzionalità di disponibilità di tre sono disponibili in Linux per le distribuzioni basate su Windows:
-   Gruppi di disponibilità AlwaysOn (estensivi)
-   Istanze del Cluster di Failover (FCI) Always On
-   [Log shipping](sql-server-linux-use-log-shipping.md)

In Windows, le istanze FCI è sempre necessario un cluster di failover di Windows Server (WSFC) sottostante. A seconda dello scenario di distribuzione, un gruppo di disponibilità in genere non richiede che un cluster WSFC sottostante, con l'eccezione nuovo variant in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Non esiste un cluster WSFC in Linux. Clustering di implementazione in Linux è illustrato di seguito [istanze Pacemaker per cluster di failover e gruppi di disponibilità AlwaysOn in Linux](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux).

## <a name="a-quick-linux-primer"></a>Verrà riportata una breve spiegazione di Linux
Mentre alcune installazioni Linux possono essere installate con un'interfaccia, la maggior parte non sono, vale a dire che quasi tutte le funzioni a livello del sistema operativo viene eseguita tramite riga di comando. Il termine comune per questa riga di comando nel mondo Linux è un *shell bash*.

In Linux, molti comandi devono essere eseguite con privilegi elevati, analogamente a molte operazioni devono essere eseguite in Windows Server come amministratore. Esistono due metodi principali per l'esecuzione con privilegi elevati:
1. Eseguire nel contesto dell'utente appropriato. Per modificare a un altro utente, utilizzare il comando `su`. Se `su` viene eseguita in modo autonomo senza un nome utente, purché si conosce la password, a questo punto sarà in una shell come *radice*.
   
2. Le più comuni e sicurezza consapevole per eseguire operazioni consiste nell'utilizzare `sudo` prima di eseguire alcuna operazione. Molti degli esempi in questo articolo usa `sudo`.

Alcuni comandi comuni, ognuno dei quali dispone di vari commutatori e le opzioni che possono essere individuate online:
-   `cd`: modificare la directory
-   `chmod`: modificare le autorizzazioni di un file o directory
-   `chown`: modificare la proprietà di un file o directory
-   `ls`: Mostra il contenuto di una directory
-   `mkdir`: creare una cartella (directory) in un'unità
-   `mv`: spostare un file da una posizione a un'altra
-   `ps`– Mostra tutti i processi di lavoro
-   `rm`: elimina un file in un server locale
-   `rmdir`: Elimina una cartella (directory)
-   `systemctl`-avviare, arrestare o abilitare i servizi
-   Comandi dell'editor di testo. In Linux, sono disponibili varie opzioni di editor di testo, ad esempio vi ed emacs.

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>Attività comuni per le configurazioni di disponibilità di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] su Linux
In questa sezione vengono descritte attività comuni a tutti i basati su Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] le distribuzioni.

### <a name="ensure-that-files-can-be-copied"></a>Verificare che possono essere copiati i file
Una cosa che chiunque utilizzando [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in Linux deve essere in grado di eseguire file di copia da un server a un altro. Questa attività è molto importante per le configurazioni del gruppo di disponibilità.

Ad esempio problemi di autorizzazione può essere presente in Linux, nonché le installazioni basate su Windows. Tuttavia, chi ha familiarità con la procedura per copiare da un server a un server in Windows potrebbero non avere familiarità con la modalità con cui viene eseguito in Linux. Un metodo comune consiste nell'utilizzare l'utilità della riga di comando `scp`, che è l'acronimo di copia sicuro. Dietro le quinte, `scp` utilizza OpenSSH. SSH è l'acronimo di shell protetta. A seconda della distribuzione di Linux, OpenSSH stesso potrebbe non essere installato. In caso contrario, OpenSSH dovrà essere installato per primo. Per ulteriori informazioni sulla configurazione OpenSSH, vedere le informazioni su uno dei collegamenti seguente per ogni distribuzione:
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-OpenSSH.html)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Quando si utilizza `scp`, è necessario fornire le credenziali del server se non è l'origine o destinazione. Ad esempio, l'utilizzo

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

Copia il file MyAGCert.cer nella cartella specificata in altro server. Si noti che è necessario disporre delle autorizzazioni: ed eventualmente: proprietà del file da copiare, quindi `chown` deve inoltre essere utilizzata prima della copia. Analogamente, sul lato di ricezione, l'utente deve accedere per modificare il file. Ad esempio, per ripristinare i file di certificato, il `mssql` utente deve essere in grado di accedervi.

Samba, vale a dire la variante Linux del blocco di messaggi server (SMB), può anche essere utilizzato per creare condivisioni accede, ad esempio i percorsi UNC `\\SERVERNAME\SHARE`. Per ulteriori informazioni sulla configurazione Samba, vedere le informazioni su uno dei collegamenti seguente per ogni distribuzione:
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

Possono essere utilizzate anche i basati su Windows condivisioni SMB; Condivisioni SMB non è necessario essere basati su Linux, purché la parte client di Samba sia configurata correttamente nel server Linux ospita [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] e la condivisione dispone di diritti di accesso. Per quelle presenti in un ambiente misto, sarebbe possibile sfruttare l'infrastruttura esistente per basati su Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] le distribuzioni.

Un aspetto importante è che la versione di Samba distribuita deve essere conforme con SMB 3.0. Quando è stato aggiunto il supporto SMB in [!INCLUDE[sssql11-md](../includes/sssql11-md.md)], è necessario tutte le condivisioni per supportare SMB 3.0. Se si utilizza Samba per la condivisione e non a Windows Server, deve utilizzare la condivisione di Samba Samba 4.0 o versione successiva e idealmente 4.3 o versioni successiva, che supporta SMB 3.1.1. È un'ottima fonte di informazioni su SMB e Linux [SMB3 in Samba](http://events.linuxfoundation.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf).

Infine, utilizza una condivisione di rete file system (NFS) è un'opzione. Utilizzo di NFS, non è un'opzione in distribuzioni basate su Windows di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]e può essere utilizzato solo per le distribuzioni basate su Linux.

### <a name="configure-the-firewall"></a>Configurare il firewall
Simile a Windows, le distribuzioni Linux dispone di un firewall incorporato. Se l'azienda Usa un firewall esterno per i server, disattivare il firewall in Linux possono essere accettabili. Tuttavia, indipendentemente dal fatto in cui il firewall è abilitato, è necessario aprire porte. Nella tabella seguente illustra le porte comuni necessari per disponibilità elevata [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] le distribuzioni di Linux.

| Numero di porta | Tipo     | Description                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS – `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | Samba (se usati): Mapper di endpoint                                                                                          |
| 137         | UDP      | Samba (se usati)-servizio nomi NetBIOS                                                                                      |
| 138         | UDP      | Samba (se usati) – datagrammi NetBIOS                                                                                          |
| 139         | TCP      | Samba (se usati) – sessione NetBIOS                                                                                           |
| 445         | TCP      | Samba (se usati) – SMB su TCP                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] : porta; predefinita Se si desidera, è possibile modificare con`mssql-conf set network.tcpport <portnumber>`                       |
| 2049        | TCP, UDP | NFS (se usate)                                                                                                               |
| 2224        | TCP      | Pacemaker – usato da`pcsd`                                                                                                |
| 3121        | TCP      | Pacemaker-richiesto se sono presenti nodi remoti Pacemaker                                                                    |
| 3260        | TCP      | Iniziatore (se usati) – iSCSI può essere modificato `/etc/iscsi/iscsid.config` (RHEL), ma deve corrispondere a una porta di destinazione software iSCSI |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -utilizzata per un endpoint del gruppo di disponibilità; porta predefinita può essere modificato durante la creazione dell'endpoint                                |
| 5403        | TCP      | Pacemaker                                                                                                                   |
| 5404        | UDP      | Pacemaker – richiesto dal Corosync se utilizzando UDP multicast                                                                     |
| 5405        | UDP      | Pacemaker – richiesto da Corosync                                                                                            |
| 21064       | TCP      | Pacemaker – necessari per le risorse tramite DLM                                                                                 |
| Variabile    | TCP      | Porta dell'endpoint; gruppo di disponibilità il valore predefinito è 5022                                                                                           |
| Variabile    | TCP      | Porta per NFS: `LOCKD_TCPPORT` (trovato nel `/etc/sysconfig/nfs` su RHEL)                                              |
| Variabile    | UDP      | Porta per NFS: `LOCKD_UDPPORT` (trovato nel `/etc/sysconfig/nfs` su RHEL)                                              |
| Variabile    | TCP/UDP  | Porta per NFS: `MOUNTD_PORT` (trovato nel `/etc/sysconfig/nfs` su RHEL)                                                |
| Variabile    | TCP/UDP  | Porta per NFS: `STATD_PORT` (trovato nel `/etc/sysconfig/nfs` su RHEL)                                                 |

Per altre porte che possono essere utilizzate da Samba, fare riferimento a [utilizzo della porta Samba](https://wiki.samba.org/index.php/Samba_Port_Usage).

Al contrario, il nome del servizio in Linux può essere inoltre aggiunto come un'eccezione anziché la porta; ad esempio, `high-availability` per Pacemaker. Se questa è la direzione in cui che si desidera proseguire, fare riferimento alla distribuzione per i nomi. Ad esempio, su RHEL è il comando per aggiungere in Pacemaker

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**Documentazione del firewall:**
-   [RHEL](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>Installare [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pacchetti per la disponibilità
In un Windows [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] installazione, alcuni componenti sono installati anche in un'installazione del motore di base, mentre altri no. In Linux, solo il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] motore viene installato come parte del processo di installazione. Tutti gli altri sono facoltativi. Per disponibilità elevata [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] istanze in Linux, è consigliabile installare due pacchetti con [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]: [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente (*mssql-server agent*) e il pacchetto di disponibilità elevata (HA) ( *MSSQL-server-a disponibilità elevata*). Mentre [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente tecnicamente facoltativo, ma [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]dell'utilità di pianificazione per i processi ed è necessario dal log shipping, è consigliabile l'installazione. Nelle installazioni basate su Windows, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente non è facoltativo.

>[!NOTE]
>Per quelli nuovi per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]dell'utilità di pianificazione di processi predefinite. È un modo comune per gli amministratori di database pianificare operazioni quali backup e altri [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] manutenzione. A differenza di un'installazione basata su Windows di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent è un servizio completamente diverso, in Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente viene eseguito nel contesto di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] stesso.

Quando estensivi o FCI sono configurate in una configurazione basata su Windows, sono compatibili con cluster. Compatibilità con cluster significa che [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] dispone della risorsa specifica le DLL che un cluster WSFC conosce (file sqagtres.dll e sqsrvres.dll per FCI, hadrres.dll per estensivi) e vengono utilizzati per il cluster WSFC per garantire che il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] funzionalità cluster è in esecuzione, e funzioni correttamente. Poiché il clustering è esterno non solo a [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ma codificare l'equivalente di una DLL di risorse per le distribuzioni basate su Linux AG e FCI Linux, Microsoft. Si tratta di *mssql-server-a disponibilità elevata* pacchetto, noto anche come il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente risorse per Pacemaker. Per installare il *mssql-server-a disponibilità elevata* del pacchetto, vedere [installare i pacchetti a disponibilità elevata e di SQL Server Agent](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages).

Gli altri pacchetti facoltativi per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] su Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ricerca Full-Text (*mssql-server-fts*) e [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*mssql server è*), non sono obbligatorio per la disponibilità elevata per un'istanza FCI o un gruppo di disponibilità.

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Pacemaker per gruppi di disponibilità AlwaysOn e le istanze cluster di failover su Linux
Come indicato in precedenza, l'unico meccanismo clustering attualmente supportato da Microsoft per estensivi e FCI è Pacemaker con Corosync. In questa sezione vengono illustrate le informazioni di base per comprendere la soluzione, nonché come pianificare e distribuire per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] configurazioni.

### <a name="ha-add-onextension-basics"></a>Nozioni fondamentali di componente aggiuntivo on/estensione a disponibilità elevata
Tutte le distribuzioni supportate attualmente fornito un'elevata disponibilità componente aggiuntivo-on/estensione, basato sul Pacemaker clustering dello stack. In questo stack include due componenti principali: Pacemaker e Corosync. Tutti i componenti dello stack sono:
-   Pacemaker-di base clustering componente, ad esempio coordinate tra i computer del cluster.
-   Corosync: un framework e un set di API che fornisce elementi quali quorum, la possibilità di processi di riavvio non riuscito e così via.
-   libQB – fornisce operazioni quali la registrazione.
-   Agente di risorse-funzionalità specifica fornita in modo che un'applicazione può essere integrato con Pacemaker.
-   Limite agente-script o funzionalità di isolare i nodi e gestirli in se si verificano problemi.
    
> [!NOTE]
> Lo stack di cluster è considerato come Pacemaker nel mondo Linux.

Questa soluzione è simile a, ma in molti modi diversi dalla distribuzione di Windows utilizzando le configurazioni in cluster. In Windows, viene creato il modulo di disponibilità di clustering, chiamata di un cluster di failover di Windows Server (WSFC), il sistema operativo e la funzionalità che consente la creazione di un cluster WSFC, il clustering di failover, è disabilitato per impostazione predefinita. In Windows, estensivi FCI si avvalgono di un cluster WSFC e condividere una stretta integrazione a causa di specifiche DLL della risorsa che viene fornito da [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Questa soluzione fortemente accoppiata è possibile in generale le perché è da un fornitore.

![](./media/sql-server-linux-ha-basics/image1.png)

In Linux, mentre ogni distribuzione supportato ha Pacemaker disponibili, ogni distribuzione personalizzare e dispongono di versioni e le implementazioni leggermente diverse. Alcune delle differenze verranno riflesse nelle istruzioni in questo articolo. Il livello di clustering è open source, pertanto anche se è disponibile con le distribuzioni, non è strettamente integrato nello stesso modo un cluster WSFC è in Windows. Ecco perché Microsoft fornisce *mssql-server-a disponibilità elevata*, in modo che [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] e lo stack Pacemaker può fornire Chiudi per, ma non esattamente uguali, esperienza per estensivi e FCI come in Windows.

Per informazioni complete sulle Pacemaker, tra cui una spiegazione più dettagliata di tutto sia con le informazioni di riferimento complete, per RHEL e SLES:
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Ubuntu non dispone di una Guida per la disponibilità.

Per ulteriori informazioni sull'intero stack, vedere anche ufficiali [pagina della documentazione Pacemaker](http://clusterlabs.org/doc/) sul sito Clusterlabs.

### <a name="pacemaker-concepts-and-terminology"></a>Terminologia e i concetti pacemaker
Questa sezione illustra i concetti e terminologia di un'implementazione Pacemaker comuni.

#### <a name="node"></a>Node
Un nodo è un server che partecipano al cluster. Un cluster Pacemaker supporta fino a 16 nodi. Questo numero può essere superato se Corosync non è in esecuzione in nodi aggiuntivi, ma è necessario per Corosync [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Pertanto, il numero massimo di nodi di un cluster può avere per qualsiasi [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-configurazione di base è 16; questo è il limite di Pacemaker e non ha nulla a che fare con limitazioni massime per estensivi o FCI imposte dal [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. 

#### <a name="resource"></a>Risorsa
Un cluster WSFC sia un cluster Pacemaker hanno il concetto di una risorsa. Una risorsa è una funzionalità specifica che viene eseguito nel contesto del cluster, ad esempio un disco o un indirizzo IP. Ad esempio, in Pacemaker risorse di FCI e gruppo di disponibilità possono ottenere create. Non è simile a quella che viene effettuata in un cluster WSFC, in cui si verifica un [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] per in un'istanza cluster di failover o una risorsa un gruppo di disponibilità quando si configura un gruppo di disponibilità, ma è non esattamente uguale a causa delle differenze di base in come [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] si integra con Pacemaker.

Pacemaker dispone di risorse standard e clone. Le risorse clone sono quelli che eseguono contemporaneamente in tutti i nodi. Un esempio sarebbe un indirizzo IP che viene eseguito su più nodi per scopi di bilanciamento del carico. Qualsiasi risorsa che viene creato per FCI utilizza una risorsa standard, poiché solo un nodo può ospitare un'istanza FCI in qualsiasi momento.

Quando viene creato un gruppo di disponibilità, richiede un tipo speciale di una risorsa di clone denominata una risorsa più stata. Mentre un gruppo di disponibilità dispone solo di una replica primaria, il gruppo di disponibilità è in esecuzione in tutti i nodi che è configurato per l'utilizzo in e può consentire, ad esempio, accesso in sola lettura. Poiché si tratta di un "attivo" uso del nodo, le risorse hanno il concetto di due stati: principale e quella secondaria. Per ulteriori informazioni, vedere [più state risorse: risorse con più modalità](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html).

#### <a name="resource-groupssets"></a>Gruppi o set di risorse
Analogamente ai ruoli in un cluster WSFC, un cluster Pacemaker ha il concetto di un gruppo di risorse. Un gruppo di risorse (denominato set in SLES) è una raccolta di risorse che funzionano insieme ed eseguire il failover da un nodo a un altro come una singola unità. Gruppi di risorse non possono contenere le risorse che sono configurate come master/slave; di conseguenza, non possono essere utilizzate per estensivi. Mentre un gruppo di risorse può essere utilizzato per le istanze FCI, non è in genere una configurazione consigliata.

#### <a name="constraints"></a>Vincoli
WSFCs dispongono di parametri diversi per le risorse, nonché elementi quali le dipendenze, che indicano il cluster WSFC di una relazione padre-figlio tra due diverse risorse. Una dipendenza è solo una regola che indica il cluster WSFC deve essere online innanzitutto la risorsa.

Un cluster Pacemaker non hanno il concetto di dipendenze, ma sono presenti vincoli. Esistono tre tipi di vincoli: condivisione del percorso, la posizione e ordinamento.
-   Consente di applicare un vincolo di condivisione percorso due risorse devono essere in esecuzione nello stesso nodo o meno.
-   Un vincolo di percorso indica il cluster Pacemaker in cui eseguire una risorsa può (o possibile).
-   Un vincolo di ordinamento indica il cluster Pacemaker l'ordine in cui devono iniziare le risorse.

> [!NOTE]
> I vincoli di condivisione del percorso non sono necessari per le risorse in un gruppo di risorse, perché tutti di questi vengono visualizzati come una singola unità.

#### <a name="quorum-fence-agents-and-stonith"></a>Quorum, agenti di limite e STONITH
Quorum in Pacemaker è simile a un cluster WSFC in concetto. Lo scopo del meccanismo di quorum di un cluster consiste nel verificare che il cluster rimarrà attivo e in esecuzione. Un cluster WSFC sia i componenti aggiuntivi a disponibilità elevata per le distribuzioni di Linux hanno il concetto di voto, in cui ogni nodo viene conteggiato quorum. Si desidera ripristinare una maggioranza dei voti, in caso contrario, in uno scenario di caso peggiore, il cluster verrà arrestato.

A differenza di un cluster WSFC, non vi è alcuna risorsa di controllo del mirroring per lavorare con un quorum. Ad esempio un cluster WSFC, l'obiettivo consiste nel mantenere il numero di votanti dispari. La configurazione quorum presenta diverse considerazioni estensivi di FCI.

WSFCs monitorare lo stato dei nodi che fanno parte e gestirli quando si verifica un problema. Nelle versioni successive di WSFCs offrono funzionalità quali la messa in quarantena a un nodo comportamento errato di un o non disponibile (nodo non è attiva, comunicazione di rete è verso il basso e così via). Sul lato di Linux, questo tipo di funzionalità viene fornito da un agente di limite. Il concetto è talvolta detta fencing. Tuttavia, questi agenti limite vengono in genere specifici per la distribuzione e spesso forniti da fornitori di hardware e alcuni fornitori di software, ad esempio quelli che forniscono gli hypervisor. Ad esempio, VMware fornisce un agente di limite che può essere utilizzato per le macchine virtuali Linux virtualizzati con vSphere.

Quorum conflitti valori equivalenti in un altro concetto chiamato STONITH e riprendere il nodo altri nell'intestazione. STONITH è necessario disporre di un cluster Pacemaker supportate in tutte le distribuzioni di Linux. Per ulteriori informazioni, vedere [conflitti in un Cluster a disponibilità elevata Red Hat](https://access.redhat.com/solutions/15575) (RHEL).

#### <a name="corosyncconf"></a>corosync.conf
Il `corosync.conf` file contiene la configurazione del cluster. Si trova in `/etc/corosync`. Durante lo svolgimento delle normali operazioni quotidiane, questo file non devono essere modificate se il cluster è configurato correttamente.

#### <a name="cluster-log-location"></a>Percorso del log del cluster
Percorsi dei log per i cluster Pacemaker diversi a seconda della distribuzione.
-   RHEL e SLES-`/var/log/cluster/corosync.log`
-   Ubuntu:`/var/log/corosync/corosync.log`

Per modificare il percorso di registrazione predefinito, modificare `corosync.conf`.

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Piano per i cluster Pacemaker[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Questa sezione illustra le considerazioni di pianificazione per un cluster Pacemaker.

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Per i cluster di virtualizzazione Pacemaker basati su Linux[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Utilizzo di macchine virtuali per la distribuzione basata su Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] le distribuzioni per estensivi e FCI è coperto dalle stesse regole relative controparti basati su Windows. È un set di regole per il supporto di base virtualizzato [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] fornite da Microsoft in distribuzioni [956893 KB di supporto Microsoft](https://support.microsoft.com/en-us/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment). Hypervisor diversi, ad esempio Microsoft Hyper-V e VMware ESXi abbia varianze diverse in cui, a causa delle differenze tra le piattaforme autonomamente.

Se si desidera estensivi e FCI nella virtualizzazione, verificare che l'anti-affinità è impostata per i nodi di un determinato cluster Pacemaker. Quando è configurato per la disponibilità elevata in un gruppo di disponibilità o FCI sulla configurazione, le macchine virtuali che ospitano [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] mai deve essere in esecuzione nello stesso host dell'hypervisor. Ad esempio, se viene distribuita una FCI di due nodi, sarebbe necessario essere *almeno* tre host hypervisor in modo che in un punto per una delle macchine virtuali che ospita un nodo per passare guasto di un host, soprattutto se le opzioni di funzionalità come Live Migrazione o vMotion.

Per ulteriori informazioni, consultare:
-   Documentazione di Hyper-V: [tramite Clustering Guest per la disponibilità elevata](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   White paper (scritto per le distribuzioni basate su Windows, ma la maggior parte dei concetti ancora applicare) – [pianificazione della disponibilità elevata, applicazioni di importanza critica le distribuzioni di SQL Server con VMware vSphere](http://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

>[!NOTE]
>RHEL con un cluster Pacemaker con STONITH non è ancora supportata da Hyper-V. Fino a quando non supportata, per ulteriori informazioni e aggiornamenti, consultare [criteri di supporto per i cluster di disponibilità elevata RHEL](https://access.redhat.com/articles/29440#3physical_host_mixing).

### <a name="networking"></a>Funzionalità di rete
A differenza di un WSFC Pacemaker non richiede un nome dedicato o almeno un indirizzo IP dedicato per il cluster Pacemaker stesso. Estensivi e FCI richiedono indirizzi IP (vedere la documentazione relativa a ciascuno di essi per ulteriori informazioni), ma non i nomi, poiché non esiste alcuna risorsa del nome di rete. SLES consente la configurazione di un indirizzo IP per l'amministrazione, ma non è necessaria, come si può notare [creare il cluster Pacemaker](sql-server-linux-deploy-pacemaker-cluster.md#create).

Ad esempio un cluster WSFC, Pacemaker preferisce rete ridondante, vale a dire distinti di rete (NIC o pNICs per fisica) con indirizzi IP singoli. In termini di configurazione del cluster, ogni indirizzo IP avrebbe ciò che viene definito il proprio anello. Tuttavia, come con WSFCs oggi, molte implementazioni virtualizzate o nel cloud pubblico in cui non è disponibile una sola virtualizzato NIC (vNIC) presentati al server. Se tutti pNICs e vNICs connessi allo stesso commutatore fisico o virtuale, non è nessuna true ridondanza a livello di rete, pertanto la configurazione di più schede di rete è un po' di un effetto ottico alla macchina virtuale. La ridondanza di rete è incorporata in genere hypervisor per le distribuzioni virtualizzate e sicuramente è incorporata nel cloud pubblico.

Una differenza con più schede di rete e Pacemaker rispetto a un cluster WSFC è che Pacemaker supporta più indirizzi IP nella stessa subnet, a differenza di un cluster WSFC. Per ulteriori informazioni su più subnet e i cluster Linux, vedere l'articolo [configurare più subnet](sql-server-linux-configure-multiple-subnet.md).

### <a name="quorum-and-stonith"></a>Quorum e STONITH
Configurazione quorum e ai requisiti correlati al gruppo di disponibilità o specifiche per FCI distribuzioni di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

STONITH è obbligatorio per un cluster Pacemaker supportate. Per configurare STONITH, utilizzare la documentazione fornita dalla distribuzione. Un esempio è in [Fencing basate sull'archiviazione](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html) per SLES. È inoltre disponibile un agente STONITH per VMware vCenter per le soluzioni basate su ESXI. Per ulteriori informazioni, vedere [Stonith plug-in agente per VMWare VM VCenter SOAP conflitti (Unofficial)](https://github.com/olafrv/fence_vmware_soap).

> [!NOTE]
> Al momento della stesura di questo articolo, Hyper-V non dispone di una soluzione per STONITH. Questo vale per distribuzioni locali e influisce anche sulle distribuzioni di Pacemaker basato su Azure con alcune distribuzioni, ad esempio RHEL.

### <a name="interoperability"></a>Interoperabilità
Questa sezione illustra come un cluster basati su Linux, è possibile interagire con un cluster WSFC o con altre distribuzioni di Linux.

#### <a name="wsfc"></a>WSFC
Attualmente, non sarà più diretto per un cluster WSFC e un cluster Pacemaker. Ciò significa che non è possibile creare un gruppo di disponibilità o FCI che funziona in un WSFC e Pacemaker. Tuttavia, esistono due soluzioni di interoperabilità, che sono progettati per estensivi. L'unico modo che un'istanza FCI possono partecipare a una configurazione multipiattaforma è se è inclusa come un'istanza in uno di questi due scenari:
-   Un gruppo di disponibilità con un tipo di cluster None. Per ulteriori informazioni, vedere Windows [documentazione dei gruppi di disponibilità](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).
-   AG distribuite, ovvero un tipo speciale di gruppo di disponibilità che consente a due diversi estensivi deve essere configurata come proprio gruppo di disponibilità. Per ulteriori informazioni su estensivi distribuite, vedere la documentazione [gruppi di disponibilità distribuiti](../database-engine/availability-groups/windows/distributed-availability-groups.md).

#### <a name="other-linux-distributions"></a>Altre distribuzioni Linux
In Linux, tutti i nodi di un cluster Pacemaker devono essere nella stessa distribuzione. Ad esempio, ciò significa che un nodo RHEL non può essere parte di un cluster Pacemaker che dispone di un nodo SLES. Il motivo principale per l'oggetto è stato indicato in precedenza: le distribuzioni possono avere diverse versioni e funzionalità, in modo aspetti potrebbe non funzionare correttamente. Combinazione di distribuzioni ha la stessa storia come la combinazione di WSFCs e Linux: nessuno o distribuito estensivi.

## <a name="next-steps"></a>Passaggi successivi
[Distribuire un cluster Pacemaker per SQL Server in Linux](sql-server-linux-deploy-pacemaker-cluster.md)
