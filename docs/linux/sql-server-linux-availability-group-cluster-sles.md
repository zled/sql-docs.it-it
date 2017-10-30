---
title: "Configurare SLES Cluster per il gruppo di disponibilità di SQL Server | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 05/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 85180155-6726-4f42-ba57-200bf1e15f4d
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 50a2633790b9878a8be2a9a3c417fc877a37633d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="configure-sles-cluster-for-sql-server-availability-group"></a>Configurare SLES Cluster per il gruppo di disponibilità di SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Questa guida vengono fornite istruzioni per creare un cluster di tre nodi per SQL Server su SUSE Linux Enterprise Server (SLES) 12 SP2. Per la disponibilità elevata, un gruppo di disponibilità in Linux richiede tre nodi, vedere [elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](sql-server-linux-availability-group-ha.md). Il livello di clustering si basa su SUSE [estensione a disponibilità elevata (Georgiano)](https://www.suse.com/products/highavailability) compilato in cima [Pacemaker](http://clusterlabs.org/). 

Per ulteriori informazioni su configurazione cluster, le opzioni di agente di risorse, gestione, procedure consigliate e indicazioni, vedere [SUSE Linux Enterprise ad alta disponibilità estensione 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

>[!NOTE]
>A questo punto, integrazione di SQL Server con Pacemaker in Linux non è accoppiata come con WSFC in Windows. Il servizio SQL Server in Linux non è compatibile con cluster. Pacemaker controlla tutti dell'orchestrazione di risorse del cluster, tra cui la risorsa del gruppo di disponibilità. In Linux, deve fare affidamento su sempre su disponibilità gruppo viste a gestione dinamica (DMV) che forniscono informazioni del cluster come Sys.dm hadr_cluster. Inoltre, il nome di rete virtuale è specifico di WSFC, è disponibile un equivalente dello stesso in Pacemaker. È comunque possibile creare un listener per poterlo utilizzare per la riconnessione dopo il failover trasparente, ma è necessario registrare manualmente il nome del listener nel server DNS con l'indirizzo IP utilizzato per creare la risorsa IP virtuale (come illustrato di seguito).


## <a name="roadmap"></a>Guida di orientamento

I passaggi per creare un gruppo di disponibilità nel server Linux per la disponibilità elevata sono diversi da quelle in un cluster di failover di Windows Server. L'elenco seguente descrive i passaggi di alto livelli: 

1. [Configurare SQL Server nei nodi del cluster](sql-server-linux-setup.md).

2. [Creare il gruppo di disponibilità](sql-server-linux-availability-group-failover-ha.md). 

3. Configurare un gestore di risorse cluster, ad esempio Pacemaker. Queste istruzioni sono in questo documento.
   
   Il modo per configurare un gestore di risorse cluster dipende dalla distribuzione Linux specifica. 

   >[!IMPORTANT]
   >Gli ambienti di produzione richiedono un agente di geofencing, ad esempio STONITH per la disponibilità elevata. Dimostrazione di questa documentazione non utilizzano agenti fencing. Dimostrazioni sono per i test e convalida solo. 
   
   >Un cluster Pacemaker utilizza fencing per restituire il cluster in uno stato noto. Il modo per configurare fencing varia a seconda della distribuzione e l'ambiente. In questo momento, fencing non è disponibile in alcuni ambienti cloud. Vedere [estensione la disponibilità elevata di SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. [Aggiungere il gruppo di disponibilità come una risorsa del cluster](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server). 

## <a name="prerequisites"></a>Prerequisiti

Per completare lo scenario end-to-end riportato di seguito è necessario tre computer per distribuire il cluster di tre nodi. La procedura seguente descrive come configurare i server.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Installare e configurare il sistema operativo in ogni nodo del cluster 

Il primo passaggio consiste nel configurare il sistema operativo nei nodi del cluster. Per questa procedura dettagliata, è possibile utilizzare SLES 12 SP2 con una sottoscrizione valida per il componente aggiuntivo a disponibilità elevata.

### <a name="install-and-configure-sql-server-service-on-each-cluster-node"></a>Installare e configurare il servizio SQL Server in ogni nodo del cluster

1. Installare e configurare il servizio SQL Server in tutti i nodi. Per informazioni dettagliate vedere [installazione di SQL Server in Linux](sql-server-linux-setup.md).

1. Specificare un nodo primari e di altri nodi come database secondari. Utilizzare questi termini all'interno di questa Guida.

1. Assicurarsi che i nodi che verranno da parte del cluster possono comunicare tra loro.

   Nell'esempio seguente `/etc/hosts` aggiunte tre nodi denominati SLES1, SLES2 e SLES3.

   ```
   127.0.0.1   localhost
   10.128.16.33 SLES1
   10.128.16.77 SLES2
   10.128.16.22 SLES3
   ```

   Tutti i nodi del cluster devono essere in grado di accedere ai loro via SSH. Strumenti come `hb_report` o `crm_report` (per la risoluzione dei problemi) e cronologia Esplora del Hawk richiedono l'accesso SSH passwordless tra i nodi, in caso contrario è possibile raccogliere solo i dati dal nodo corrente. Nel caso in cui si utilizza una porta SSH non standard, utilizzare l'opzione -X (vedere `man` pagina). Ad esempio, se la porta SSH è 3479, richiamare un `crm_report` con:

   ```bash
   sudo crm_report -X "-p 3479" [...]
   ```

   Per ulteriori informazioni, vedere il [Guida all'amministrazione SLES - sezione Miscellaneous](http://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc).


## <a name="create-a-sql-server-login-for-pacemaker"></a>Creare un account di accesso di SQL Server per Pacemaker

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="configure-an-always-on-availability-group"></a>Configurare un gruppo di disponibilità Always On

In server Linux configurare il gruppo di disponibilità e quindi configurare le risorse del cluster. Per configurare il gruppo di disponibilità, vedere [Configura gruppo di disponibilità AlwaysOn per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installare e configurare Pacemaker su ogni nodo del cluster

1. Installare l'estensione per la disponibilità elevata

   Per riferimento, vedere [l'installazione di SUSE Linux Enterprise Server e l'estensione di disponibilità elevata](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.installation)

1. Installare il pacchetto dell'agente di risorse SQL Server in entrambi i nodi.

   ```bash
   sudo zypper install mssql-server-ha
   ```

## <a name="set-up-the-first-node"></a>Impostare il primo nodo

   Fare riferimento a [le istruzioni di installazione SLES](http://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node)

1. Accedere come `root` per la macchina virtuale che si desidera utilizzare come nodo del cluster o fisica.
2. Avviare lo script di avvio eseguendo:
   ```bash
   sudo ha-cluster-init
   ```

   NTP non è stato configurato per l'avvio in fase di avvio, verrà visualizzato un messaggio. 

   Se si decide di continuare, lo script verrà automaticamente generare le chiavi per l'accesso SSH e per lo strumento di sincronizzazione Csync2 e avviare i servizi necessari per entrambi. 

3. Per configurare il livello di comunicazione del cluster (Corosync): 

   A. Immettere un indirizzo di rete da associare. Per impostazione predefinita, lo script propone di eth0 l'indirizzo di rete. In alternativa, immettere un indirizzo di rete diversi, ad esempio l'indirizzo di bond0. 

   B. Immettere un indirizzo multicast. Lo script propone un indirizzo casuale che è possibile utilizzare come valore predefinito. 

   c. Immettere una porta multicast. Lo script viene proposto 5405 come predefinito. 

   d. Per configurare `SBD ()`, immettere un percorso persistente per la partizione del dispositivo che si desidera utilizzare per SBD blocco. Il percorso deve essere coerenza in tutti i nodi del cluster. 
   Infine, lo script avvia il servizio Pacemaker per connettere il cluster a un nodo e abilitare l'interfaccia di gestione Web Hawk2. L'URL da utilizzare per Hawk2 viene visualizzato sullo schermo. 

4. Per i dettagli del processo di installazione, controllare `/var/log/sleha-bootstrap.log`. È ora disponibile un cluster a un nodo in esecuzione. Controllare lo stato del cluster con stato crm:

   ```bash
   sudo crm status
   ```

   È inoltre possibile visualizzare la configurazione del cluster con `crm configure show xml` o `crm configure show`.

5. La procedura di bootstrap crea un utente di Linux denominato hacluster con la password di linux. Sostituire la password predefinita con una protezione appena possibile: 

   ```bash
   sudo passwd hacluster
   ```

## <a name="add-nodes-to-the-existing-cluster"></a>Aggiungere nodi al cluster esistente

Se si dispone di un cluster che esegue con uno o più nodi, è possibile aggiungere più nodi del cluster con lo script di avvio a disponibilità elevata del cluster-join. Lo script è necessario solo l'accesso a un nodo del cluster esistente e verrà completata automaticamente l'installazione di base sul computer corrente. Attenersi alla procedura seguente:

Se sono stati configurati i nodi del cluster esistente con il `YaST` modulo del cluster, assicurarsi che siano soddisfatti i prerequisiti seguenti prima di eseguire `ha-cluster-join`:
- L'utente root nei nodi esistenti dispone delle chiavi SSH per passwordless account di accesso. 
- `Csync2`viene configurato nei nodi esistenti. Per informazioni dettagliate, vedere configurazione Csync2 con YaST. 

1. Accedere come radice per la macchina virtuale dovrebbe da aggiungere al cluster o fisica. 
2. Avviare lo script di avvio eseguendo: 

   ```bash
   sudo ha-cluster-join
   ```

   NTP non è stato configurato per l'avvio in fase di avvio, verrà visualizzato un messaggio. 

3. Se si decide di continuare, verrà richiesto per l'indirizzo IP di un nodo esistente. Immettere l'indirizzo IP. 

4. Se non è già stato configurato un accesso SSH passwordless tra entrambi i computer, verrà inoltre richiesto per la password radice del nodo esistente. 

   Dopo l'accesso al nodo specificato, lo script verrà copiare la configurazione di Corosync, configurare SSH e `Csync2`e verrà portare online la macchina corrente come nuovo nodo del cluster. Inoltre, verrà avviato il servizio richiesto per Hawk. Se è stata configurata l'archiviazione condivisa con `OCFS2`, verrà creato automaticamente anche la directory del punto di montaggio per il `OCFS2` del file system. 

5. Ripetere i passaggi precedenti per tutti i computer che si desidera aggiungere al cluster. 

6. Per i dettagli del processo, controllare `/var/log/ha-cluster-bootstrap.log`. 

1. Controllare lo stato del cluster con `sudo crm status`. Se il secondo nodo è stato aggiunto correttamente, l'output sarà simile al seguente:

   ```bash
   sudo crm status
   
   3 nodes configured
   1 resource configured
   Online: [ SLES1 SLES2 SLES3]
   Full list of resources:   
   admin_addr     (ocf::heartbeat:IPaddr2):       Started node1
   ```

   >[!NOTE]
   >`admin_addr`è la risorsa cluster IP virtuale configurato durante l'installazione iniziale a un nodo del cluster.

Dopo avere aggiunto tutti i nodi, controllare se è necessario modificare i criteri di quorum no nelle opzioni di cluster globale. Questo è particolarmente importante per i cluster a due nodi. Per ulteriori informazioni, fare riferimento alla sezione 4.1.2, l'opzione no-quorum-policy. 

## <a name="set-cluster-property-start-failure-is-fatal-to-false"></a>Impostare la proprietà cluster start-errore-è-errore irreversibile per false

`Start-failure-is-fatal`indica se un errore di avvio di una risorsa in un nodo impedisce ulteriori tentativi di avvio in tale nodo. Se impostato su `false`, il cluster stabilirà se provare ad avviare nello stesso nodo in base alle corrente conteggio e la migrazione soglia di errore della risorsa. In tal caso, dopo che si verifica il failover, Pacemaker tenterà di avviare la risorsa del gruppo di disponibilità sulla prima primario quando l'istanza SQL è disponibile. Pacemaker si occuperà di abbassamento di livello la replica secondaria e verrà automaticamente aggiunto nuovamente il gruppo di disponibilità. Inoltre, se `start-failure-is-fatal` è impostato su `false`, il cluster eseguirà il fallback per i limiti configurati failcount configurati con la soglia di migrazione, pertanto è necessario verificare che predefinito per il limite di migrazione viene aggiornato di conseguenza.

Per aggiornare il valore della proprietà per l'esecuzione false:
```bash
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
Se la proprietà ha il valore predefinito di `true`, se il primo tentativo di avviare la risorsa non, l'intervento dell'utente è obbligatorio dopo un failover automatico per eseguire la pulizia il conteggio degli errori di risorse e reimposta la configurazione mediante: `sudo crm resource cleanup <resourceName>` comando.

Per ulteriori informazioni sulle proprietà del cluster Pacemaker vedere [la configurazione di risorse Cluster](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

# <a name="configure-fencing-stonith"></a>Configurare fencing (STONITH)
I fornitori di cluster pacemaker richiedono STONITH deve essere abilitata e un dispositivo fencing configurato per l'installazione del cluster supportate. Quando il gestore delle risorse cluster non è possibile determinare lo stato di un nodo o di una risorsa in un nodo, fencing viene utilizzato per visualizzare di nuovo il cluster in uno stato noto.
Fencing livello risorse principalmente garantisce che non vi sia alcun danneggiamento dei dati in caso di interruzione tramite la configurazione di una risorsa. È possibile utilizzare fencing livello di risorse, ad esempio, con DRBD (Distributed replicati blocco dispositivo) per contrassegnare il disco in un nodo come obsoleta quando il collegamento di comunicazione si arresta.
Fencing livello di nodo garantisce che un nodo non viene eseguito tutte le risorse. In tal caso, reimpostare il nodo e l'implementazione Pacemaker di esso viene chiamato STONITH (che è l'acronimo di "riprendere l'altro nodo nell'intestazione"). Pacemaker supporta una vasta gamma di dispositivi fencing, ad esempio un continuità o gestione delle schede di interfaccia di per i server.
Per ulteriori informazioni, vedere [cluster Pacemaker novo](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html), [Fencing e Stonith](http://clusterlabs.org/doc/crm_fencing.html) e [documentazione SUSE a disponibilità elevata: Fencing e STONITH](https://www.suse.com/documentation/sle_ha/book_sleha/data/cha_ha_fencing.html).

In fase di inizializzazione del cluster, STONITH è disabilitata se non viene rilevata alcuna configurazione. Può essere abilitata in un secondo momento mediante l'esecuzione di comando seguente

```bash
sudo crm configure property stonith-enabled=true
```
  
>[!IMPORTANT]
>La disattivazione STONITH è solo a scopo di test. Se si prevede di utilizzare Pacemaker in un ambiente di produzione, pianificare un'implementazione STONITH a seconda dell'ambiente e mantenerla abilitato. Si noti che SUSE non fornisce fencing agenti per ambienti cloud (Azure inclusi) o Hyper-V. Consequentially, il fornitore del cluster non offre il supporto per i cluster di produzione in esecuzione in questi ambienti. Stiamo lavorando su una soluzione per questo spazio che sarà disponibile nelle versioni future.


## <a name="configure-the-cluster-resources-for-sql-server"></a>Configurare le risorse del cluster per SQL Server

Fare riferimento a [SLES amministrazione Guid](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)

### <a name="create-availability-group-resource"></a>Creare una risorsa del gruppo di disponibilità

Il comando seguente crea e configura la risorsa del gruppo di disponibilità per 3 repliche del gruppo di disponibilità [ag1]. Le operazioni di monitoraggio e di un timeout devono essere specificato in modo esplicito in SLES basata sul fatto che i timeout sono altamente carico di lavoro dipendenti ed è necessario adattare attentamente per ogni distribuzione.
Eseguire il comando in uno dei nodi del cluster:

1. Eseguire `crm configure` per aprire il prompt dei comandi crm:

   ```bash
   sudo crm configure 
   ```

1. Nel prompt dei crm, eseguire il comando seguente per configurare le proprietà della risorsa.

   ```bash
primitive ag_cluster \
   ocf:mssql:ag \
   params ag_name="ag1" \
   op start timeout=60s \
   op stop timeout=60s \
   op promote timeout=60s \
   op demote timeout=10s \
   op monitor timeout=60s interval=10s \
   op monitor timeout=60s interval=11s role="Master" \
   op monitor timeout=60s interval=12s role="Slave" \
   op notify timeout=60s
ms ms-ag_cluster ag_cluster \
   meta master-max="1" master-node-max="1" clone-max="3" \
  clone-node-max="1" notify="true" \
commit
   ```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

### <a name="create-virtual-ip-resource"></a>Creare la risorsa IP virtuale

Se non è stato creato la risorsa IP virtuale quando è stato eseguito `ha-cluster-init` è possibile creare ora questa risorsa. Il comando seguente crea una risorsa IP virtuale. Sostituire `<**0.0.0.0**>` con un indirizzo disponibile dalla rete e `<**24**>` con il numero di bit nella subnet mask CIDR. Eseguire in un nodo.

```bash
crm configure \
primitive admin_addr \
   ocf:heartbeat:IPaddr2 \
   params ip=<**0.0.0.0**> \
      cidr_netmask=<**24**>
```

### <a name="add-colocation-constraint"></a>Aggiungere il vincolo di percorso condiviso
Quasi ogni decisione in un cluster Pacemaker, ad esempio la scelta in cui deve essere eseguita una risorsa, viene eseguita confrontando i punteggi. I punteggi vengono calcolati per ogni risorsa e la gestione delle risorse cluster sceglie il nodo con il punteggio più alto per una particolare risorsa. (Se un nodo ha un punteggio negativo per una risorsa, la risorsa non è possibile eseguire su tale nodo.) È possibile modificare le decisioni di cluster con vincoli. I vincoli hanno un punteggio. Se un vincolo ha un punteggio inferiore a infinito, è solo un'indicazione. Un punteggio di infinito indica che è necessario. È necessario assicurarsi che primaria del gruppo di disponibilità e virtuale risorsa ip vengono quindi eseguite nello stesso host, quindi verrà definito un vincolo di percorso condiviso con un punteggio pari a infinito. 

Per impostare il vincolo di condivisione percorso per l'indirizzo IP virtuale per l'esecuzione nello stesso nodo come master, eseguire il comando seguente in un nodo:

```bash
crm configure
colocation vip_on_master inf: \
    admin_addr ms-ag_cluster:Master
commit
```

### <a name="add-ordering-constraint"></a>Aggiungi vincolo di ordinamento
Il vincolo di condivisione del percorso include un vincolo di ordinamento implicito. Sposta la risorsa IP virtuale prima di spostare la risorsa del gruppo di disponibilità. Per impostazione predefinita è la sequenza di eventi: 

1. Risorsa problemi utente eseguire la migrazione a principale del gruppo di disponibilità da node1 a node2.
2. La risorsa IP virtuale viene arrestata nel nodo 1.
3. La risorsa IP virtuale viene avviato sul nodo 2. A questo punto, l'indirizzo IP temporaneamente punti al nodo 2 mentre il nodo 2 è ancora un failover precedente secondario. 
4. Abbassamento di livello principale del gruppo di disponibilità nel nodo 1 per l'istanza slave.
5. L'istanza slave gruppo di disponibilità sul nodo 2 venga innalzato di livello master. 

Per evitare temporaneamente che puntano al nodo con il database secondario precedente failover l'indirizzo IP, aggiungere un vincolo di ordinamento. Per aggiungere un vincolo di ordinamento, eseguire il comando seguente in un nodo: 

```bash
crm crm configure \
   order ag_first inf: ms-ag_cluster:promote admin_addr:start
```


>[!IMPORTANT]
>Dopo la configurazione del cluster e aggiungere il gruppo di disponibilità come risorsa cluster, è possibile usare Transact-SQL per il failover delle risorse del gruppo di disponibilità. Risorse del cluster di SQL Server in Linux non sono collegate come strettamente con il sistema operativo come se fossero in un Windows Server Failover Cluster (WSFC). Servizio SQL Server non riconosce la presenza del cluster. Tutte le orchestrazioni viene eseguita tramite gli strumenti di gestione di cluster. In SLES utilizzare `crm`. 

Eseguire manualmente il failover del gruppo di disponibilità con `crm`. Non avviare il failover con Transact-SQL. Per istruzioni, vedere [Failover](sql-server-linux-availability-group-failover-ha.md#failover).


Per ulteriori informazioni, vedere:
- [La gestione delle risorse cluster](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm).   
- [Disponibilità elevata concetti](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.concepts)
- [Riferimento rapido pacemaker](https://github.com/ClusterLabs/pacemaker/blob/master/doc/pcs-crmsh-quick-ref.md) 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Passaggi successivi

[Utilizzare il gruppo di disponibilità elevata](sql-server-linux-availability-group-failover-ha.md)

