---
title: Configurare RHEL Cluster per il gruppo di disponibilità di SQL Server | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: b7102919-878b-4c08-a8c3-8500b7b42397
ms.openlocfilehash: 784f98acb1e8223e14d3f1e1a74e73cfdc3561bc
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="configure-rhel-cluster-for-sql-server-availability-group"></a>Configurare RHEL Cluster per il gruppo di disponibilità di SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo documento illustra come creare un cluster di gruppo di disponibilità di tre nodi per SQL Server su Red Hat Enterprise Linux. Per la disponibilità elevata, un gruppo di disponibilità in Linux richiede tre nodi, vedere [elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](sql-server-linux-availability-group-ha.md). Il livello di clustering si basa su Red Hat Enterprise Linux (RHEL) [componente aggiuntivo a disponibilità elevata](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) compilato in cima [Pacemaker](http://clusterlabs.org/). 

> [!NOTE] 
> Accesso alla documentazione completa di Red Hat richiede una sottoscrizione valida. 

Per ulteriori informazioni sulla configurazione del cluster, le opzioni di agenti di risorse e gestione, visitare [la documentazione di riferimento RHEL](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).

> [!NOTE] 
> SQL Server non è come strettamente integrato con Pacemaker su Linux e Windows Server failover clustering. Un'istanza di SQL Server non è a conoscenza del cluster. Pacemaker fornisce l'orchestrazione della risorsa cluster. Inoltre, il nome di rete virtuale è specifico per il clustering di failover di Windows Server - Pacemaker è disponibile un equivalente. Disponibilità gruppo viste a gestione dinamica (DMV) informazioni del cluster per le query restituiscono righe vuote nei cluster Pacemaker. Per creare un listener per la riconnessione dopo il failover trasparente, registrare manualmente il nome del listener in DNS con l'indirizzo IP utilizzato per creare la risorsa IP virtuale. 

Nelle sezioni seguenti viene illustrata la procedura per configurare un cluster Pacemaker e aggiungere un gruppo di disponibilità come risorsa nel cluster per la disponibilità elevata.

## <a name="roadmap"></a>Guida di orientamento

I passaggi per creare un gruppo di disponibilità nel server Linux per la disponibilità elevata sono diversi da quelle in un cluster di failover di Windows Server. L'elenco seguente descrive i passaggi generali: 

1. [Configurare SQL Server nei nodi del cluster](sql-server-linux-setup.md).

2. [Creare il gruppo di disponibilità](sql-server-linux-availability-group-configure-ha.md). 

3. Configurare un gestore di risorse cluster, ad esempio Pacemaker. Queste istruzioni sono in questo documento.
   
   Il modo per configurare un gestore di risorse cluster dipende dalla distribuzione Linux specifica. 

   >[!IMPORTANT]
   >Gli ambienti di produzione richiedono un agente di geofencing, ad esempio STONITH per la disponibilità elevata. Dimostrazione di questa documentazione non utilizzano agenti fencing. Dimostrazioni sono per i test e convalida solo. 
   
   >Un cluster Linux Usa fencing per restituire il cluster a uno stato noto. Il modo per configurare fencing varia a seconda della distribuzione e l'ambiente. Fencing non è attualmente disponibile in alcuni ambienti cloud. Per ulteriori informazioni, vedere [criteri di supporto per RHEL cluster disponibilità elevata - piattaforme di virtualizzazione](https://access.redhat.com/articles/29440).

5. [Aggiungere il gruppo di disponibilità come una risorsa del cluster](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource).  

## <a name="configure-high-availability-for-rhel"></a>Configurare la disponibilità elevata per RHEL

Per configurare la disponibilità elevata per RHEL, abilitare la sottoscrizione a disponibilità elevata e quindi configurare Pacemaker.

### <a name="enable-the-high-availability-subscription-for-rhel"></a>Attivare la sottoscrizione a disponibilità elevata per RHEL

Ogni nodo del cluster necessario avere una sottoscrizione di appropriato per RHEL e la disponibilità elevata Add. Esaminare i requisiti al [come installare i pacchetti di disponibilità elevata del cluster in Red Hat Enterprise Linux](http://access.redhat.com/solutions/45930). Seguire questi passaggi per configurare la sottoscrizione e il repository:

1. Registrare il sistema.

   ```bash
   sudo subscription-manager register
   ```

   Fornire il nome utente e password.   

1. Elenca i pool disponibili per la registrazione.

   ```bash
   sudo subscription-manager list --available
   ```

   Dall'elenco di pool di disponibili, si noti l'ID del pool per la sottoscrizione a disponibilità elevata.

1. Aggiornare lo script seguente. Sostituire `<pool id>` con l'ID del pool per la disponibilità elevata nel passaggio precedente. Eseguire lo script per collegare la sottoscrizione.

   ```bash
   sudo subscription-manager attach --pool=<pool id>
   ```

1. Abilitare il repository.

   ```bash
   sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
   ```

Per ulteriori informazioni, vedere [Cluster a disponibilità elevata Pacemaker – l'Open Source,](http://www.opensourcerers.org/pacemaker-the-open-source-high-availability-cluster/). 

Dopo aver configurato la sottoscrizione, completare i passaggi seguenti per configurare Pacemaker:

### <a name="configure-pacemaker"></a>Configurare Pacemaker

Dopo aver registrato la sottoscrizione, completare i passaggi seguenti per configurare Pacemaker:
   
[!INCLUDE [RHEL-Configure-Pacemaker](../includes/ss-linux-cluster-pacemaker-configure-rhel.md)]

Dopo aver configurato il Pacemaker, utilizzare `pcs` per interagire con il cluster. Eseguire tutti i comandi in un nodo dal cluster. 

## <a name="configure-fencing-stonith"></a>Configurare fencing (STONITH)

I fornitori di cluster pacemaker richiedono STONITH deve essere abilitata e un dispositivo fencing configurato per l'installazione del cluster supportate. STONITH è l'acronimo di "riprendere l'altro nodo nell'intestazione". Quando il gestore delle risorse cluster non è possibile determinare lo stato di un nodo o di una risorsa in un nodo, fencing porta nuovamente al cluster di uno stato noto.

Fencing livello risorse non assicura che sia presente alcun danneggiamento dei dati in caso di interruzione tramite la configurazione di una risorsa. Ad esempio, è possibile utilizzare fencing livello di risorse per contrassegnare il disco in un nodo come obsoleta quando il collegamento di comunicazione si arresta. 

Fencing livello di nodo garantisce che un nodo non viene eseguito tutte le risorse. Questa operazione viene eseguita reimpostando il nodo. Pacemaker supporta una vasta gamma di dispositivi di conflitti. Ad esempio una schede di interfaccia alimentatore o gestione continuità per i server.

Per informazioni su STONITH e fencing, vedere gli articoli seguenti:

* [Cluster pacemaker da zero](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)
* [Fencing e STONITH](http://clusterlabs.org/doc/crm_fencing.html)
* [Componente aggiuntivo di disponibilità elevata di Red Hat con Pacemaker: conflitti](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-fencing-HAAR.html)

Poiché il livello del nodo conflitti di configurazione dipende molto dall'ambiente, è possibile disabilitarla per questa esercitazione (può essere configurato in un secondo momento). Lo script seguente disabilita fencing livello di nodo:

```bash
sudo pcs property set stonith-enabled=false
```
  
>[!IMPORTANT]
>La disattivazione STONITH è solo a scopo di test. Se si prevede di utilizzare Pacemaker in un ambiente di produzione, pianificare un'implementazione STONITH a seconda dell'ambiente e mantenerla abilitato. RHEL non fornisce fencing agenti per ambienti cloud (Azure inclusi) o Hyper-V. Consequentially, il fornitore del cluster non offre il supporto per i cluster di produzione in esecuzione in questi ambienti. Stiamo lavorando su una soluzione per questo spazio che sarà disponibile nelle versioni future.

## <a name="set-cluster-property-cluster-recheck-interval"></a>Impostare proprietà di cluster del cluster-nuova verifica del-intervallo

`cluster-recheck-interval` indica l'intervallo di polling durante il quale controlla il cluster per la modifica in parametri delle risorse, i vincoli o altre opzioni di cluster. Se una replica diventa inattiva, il cluster tenta di riavviare la replica a un intervallo che è associato il `failure-timeout` valore e il `cluster-recheck-interval` valore. Ad esempio, se `failure-timeout` è impostata su 60 secondi e `cluster-recheck-interval` è impostato su 120 secondi, il riavvio viene eseguito un tentativo a un intervallo che è maggiore di 60 secondi ma inferiore a 120 secondi. È consigliabile impostare timeout errore 60s e intervallo di nuova verifica del cluster su un valore maggiore di 60 secondi. Non è consigliabile impostare l'intervallo di nuova verifica del cluster su un valore basso.

Per aggiornare il valore della proprietà da `2 minutes` eseguire:

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Tutte le distribuzioni (inclusi RHEL 7.3 e 7.4) che usano la versione più recente disponibile Pacemaker pacchetto 1.1.18-11.el7 introducono una modifica del comportamento per l'impostazione di start-errore-è-irreversibile cluster quando il relativo valore è false. Questa modifica interessa il flusso di lavoro di failover. Se una replica primaria di cui si verifichi un'interruzione del servizio, il cluster deve eseguire il failover su una delle repliche secondarie disponibili. Al contrario, gli utenti noteranno che il cluster mantiene tenta di avviare la replica primaria non riuscita. Se il database primario non viene portato online (a causa di un'interruzione permanente), failover del cluster mai a un'altra replica secondaria disponibile. Grazie a questa modifica, una configurazione consigliata in precedenza per impostare inizio-errore-è-errore irreversibile non è più valida e l'impostazione deve essere ripristinato il valore predefinito `true`. Inoltre, la risorsa gruppo di disponibilità deve essere aggiornato per includere il `failover-timeout` proprietà. 

Per aggiornare il valore della proprietà da `true` eseguire:

```bash
sudo pcs property set start-failure-is-fatal=true
```

Per aggiornare il `ag1` proprietà della risorsa `failure-timeout` a `60s` eseguire:

```bash
pcs resource update ag1 meta failure-timeout=60s
```


Per informazioni sulle proprietà cluster Pacemaker, vedere [Pacemaker cluster proprietà](http://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-clusteropts-HAAR.html).

## <a name="create-a-sql-server-login-for-pacemaker"></a>Creare un account di accesso di SQL Server per Pacemaker

[!INCLUDE [SQL-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>Creare una risorsa del gruppo di disponibilità

Per creare la risorsa del gruppo di disponibilità, utilizzare `pcs resource create` comando e impostare le proprietà della risorsa. Il comando seguente crea un `ocf:mssql:ag` master/slave, tipo di risorsa per il gruppo di disponibilità con nome `ag1`.

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s master notify=true
``` 

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

<a name="createIP"></a>

## <a name="create-virtual-ip-resource"></a>Creare la risorsa IP virtuale

Per creare la risorsa di indirizzo IP virtuale, eseguire il comando seguente in un nodo. Utilizzare un indirizzo IP statico disponibile dalla rete. Sostituire l'indirizzo IP tra `<10.128.16.240>` con un indirizzo IP valido.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Nessun nome server virtuale è equivalente al Pacemaker. Per utilizzare una stringa di connessione che punta a un nome di server stringa anziché un indirizzo IP, registrare il nome del server virtuale desiderata e l'indirizzo di risorse IP virtuale nel DNS. Per le configurazioni di ripristino di emergenza, registrare il nome del server virtuale desiderato e l'indirizzo IP con i server DNS primario sia del sito di ripristino di emergenza.

## <a name="add-colocation-constraint"></a>Aggiungere il vincolo di percorso condiviso

Quasi ogni decisione in un cluster Pacemaker, ad esempio la scelta in cui deve essere eseguita una risorsa, viene eseguita confrontando i punteggi. I punteggi vengono calcolati per ogni risorsa. Il gestore delle risorse cluster sceglie il nodo con il punteggio più alto per una particolare risorsa. Se un nodo ha un punteggio negativo per una risorsa, la risorsa non è possibile eseguire su tale nodo.

In un cluster pacemaker, è possibile modificare le decisioni di cluster con vincoli. I vincoli hanno un punteggio. Se un vincolo ha un punteggio minore `INFINITY`, Pacemaker viene gestito come indicazione. Un punteggio pari a `INFINITY` è obbligatorio.

Per assicurarsi che la replica primaria e le risorse di indirizzo ip virtuale eseguono nello stesso host, definire un vincolo di percorso condiviso con un punteggio di infinito. Per aggiungere il vincolo di percorso condiviso, eseguire il comando seguente in un nodo.

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>Aggiungi vincolo di ordinamento

Il vincolo di condivisione del percorso include un vincolo di ordinamento implicito. Sposta la risorsa IP virtuale prima di spostare la risorsa del gruppo di disponibilità. Per impostazione predefinita è la sequenza di eventi:

1. Problemi relativi all'utente `pcs resource move` al gruppo di disponibilità primario da node1 a node2.
1. La risorsa IP virtuale viene arrestata nel nodo 1.
1. La risorsa IP virtuale viene avviato sul nodo 2.
  
   >[!NOTE]
   >A questo punto, l'indirizzo IP temporaneamente punti al nodo 2 mentre il nodo 2 è ancora un failover precedente secondario. 
   
1. Il gruppo di disponibilità primario nel nodo 1 viene abbassato a quello secondario.
1. Il gruppo di disponibilità secondario sul nodo 2 viene promossa a primaria. 

Per evitare temporaneamente che puntano al nodo con il database secondario precedente failover l'indirizzo IP, aggiungere un vincolo di ordinamento. 

Per aggiungere un vincolo di ordinamento, eseguire il comando seguente in un nodo:

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>Dopo la configurazione del cluster e aggiungere il gruppo di disponibilità come risorsa cluster, è possibile usare Transact-SQL per il failover delle risorse del gruppo di disponibilità. Risorse del cluster di SQL Server in Linux non sono collegate come strettamente con il sistema operativo come se fossero in un Windows Server Failover Cluster (WSFC). Servizio SQL Server non riconosce la presenza del cluster. Tutte le orchestrazioni viene eseguita tramite gli strumenti di gestione di cluster. RHEL o Ubuntu utilizzare `pcs` e in uso SLES `crm` strumenti. 

Eseguire manualmente il failover del gruppo di disponibilità con `pcs`. Non avviare il failover con Transact-SQL. Per istruzioni, vedere [Failover](sql-server-linux-availability-group-failover-ha.md#failover).

## <a name="next-steps"></a>Passaggi successivi

[Utilizzare il gruppo di disponibilità elevata](sql-server-linux-availability-group-failover-ha.md)
