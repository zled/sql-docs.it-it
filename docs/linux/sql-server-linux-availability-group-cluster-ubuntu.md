---
title: Configurare il Cluster Ubuntu per il gruppo di disponibilità di SQL Server | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: dd0d6fb9-df0a-41b9-9f22-9b558b2b2233
ms.openlocfilehash: fc0dc7460c0f193cd5c053401900a21e358145ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="configure-ubuntu-cluster-and-availability-group-resource"></a>Configurare il Cluster Ubuntu e risorsa gruppo di disponibilità

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo documento illustra come creare un cluster di tre nodi in Ubuntu e aggiungere un gruppo di disponibilità creato in precedenza come risorsa nel cluster. Per la disponibilità elevata, un gruppo di disponibilità in Linux richiede tre nodi, vedere [elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](sql-server-linux-availability-group-ha.md).

> [!NOTE] 
> A questo punto, integrazione di SQL Server con Pacemaker in Linux non è accoppiata come con WSFC in Windows. All'interno di SQL, non è possibile sapere sulla presenza del cluster, tutte le orchestrazioni non rientra e il servizio viene controllato in base a un'istanza autonoma da Pacemaker. Inoltre, il nome di rete virtuale è specifico di WSFC, è disponibile un equivalente dello stesso in Pacemaker. Always On viste a gestione dinamica informazioni del cluster per le query restituiscono righe vuote. È comunque possibile creare un listener per poterlo utilizzare per la riconnessione dopo il failover trasparente, ma è necessario registrare manualmente il nome del listener nel server DNS con l'indirizzo IP utilizzato per creare la risorsa IP virtuale (come descritto nelle sezioni riportate di seguito).

Nelle sezioni seguenti viene illustrata la procedura per configurare una soluzione di cluster di failover. 

## <a name="roadmap"></a>Guida di orientamento

I passaggi per creare un gruppo di disponibilità nel server Linux per la disponibilità elevata sono diversi da quelle in un cluster di failover di Windows Server. L'elenco seguente descrive i passaggi generali: 

1. [Configurare SQL Server nei nodi del cluster](sql-server-linux-setup.md).

2. [Creare il gruppo di disponibilità](sql-server-linux-availability-group-configure-ha.md). 

3. Configurare un gestore di risorse cluster, ad esempio Pacemaker. Queste istruzioni sono in questo documento.
   
   Il modo per configurare un gestore di risorse cluster dipende dalla distribuzione Linux specifica. 

   >[!IMPORTANT]
   >Gli ambienti di produzione richiedono un agente di geofencing, ad esempio STONITH per la disponibilità elevata. Dimostrazione di questa documentazione non utilizzano agenti fencing. Dimostrazioni sono per i test e convalida solo. 
   
   >Un cluster Linux Usa fencing per restituire il cluster a uno stato noto. Il modo per configurare fencing varia a seconda della distribuzione e l'ambiente. In questo momento, fencing non è disponibile in alcuni ambienti cloud. Vedere [criteri di supporto per RHEL cluster disponibilità elevata - piattaforme di virtualizzazione](https://access.redhat.com/articles/29440) per ulteriori informazioni.

5.  [Aggiungere il gruppo di disponibilità come una risorsa del cluster](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource). 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installare e configurare Pacemaker su ogni nodo del cluster

1. In tutti i nodi aprire le porte del firewall. Aprire la porta per il servizio a disponibilità elevata Pacemaker, istanza di SQL Server e l'endpoint del gruppo di disponibilità. La porta TCP predefinita per i server che esegue SQL Server è 1433.  

   ```bash
   sudo ufw allow 2224/tcp
   sudo ufw allow 3121/tcp
   sudo ufw allow 21064/tcp
   sudo ufw allow 5405/udp
        
   sudo ufw allow 1433/tcp # Replace with TDS endpoint
   sudo ufw allow 5022/tcp # Replace with DATA_MIRRORING endpoint
        
   sudo ufw reload
   ```
   
   In alternativa, è possibile disabilitare semplicemente il firewall:
        
   ```bash
   sudo ufw disable
   ```

1. Installare i pacchetti Pacemaker. In tutti i nodi, eseguire i comandi seguenti:

   ```bash
   sudo apt-get install pacemaker pcs fence-agents resource-agents
   ```

2. Impostare la password per l'utente predefinito creato durante l'installazione dei pacchetti Pacemaker e Corosync. Usare la stessa password in tutti i nodi. 

   ```bash
   sudo passwd hacluster
   ```

## <a name="enable-and-start-pcsd-service-and-pacemaker"></a>Abilitare e avviare il servizio pcsd e Pacemaker

Il seguente comando abilita e avvia pacemaker e pcsd servizio. Eseguire in tutti i nodi. In questo modo i nodi a partecipare di nuovo il cluster dopo il riavvio. 

```bash
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl enable pacemaker
```
>[!NOTE]
>Comando pacemaker Enable potrebbe completare con l'errore 'pacemaker avvio predefinita non contiene alcun runlevels, l'interruzione'. Si tratta puramente informativo, può continuare la configurazione del cluster. 

## <a name="create-the-cluster"></a>Creare il Cluster

1. Rimuovere qualsiasi configurazione esistente del cluster da tutti i nodi. 

   In esecuzione 'PC apt get installa sudo' Installa pacemaker, corosync e PC nello stesso momento e viene avviata l'esecuzione di tutte le 3 dei servizi.  Avvio corosync genera un modello di ' / etc/cluster/corosync.conf' file.  Passaggi successivi di esito positivo di questo file non devono essere presenti: la soluzione alternativa consiste nell'arrestare pacemaker / corosync ed eliminare ' / etc/cluster/corosync.conf', e quindi passaggi successivi completata correttamente. 'PC cluster destroy' svolge la stessa funzione e utilizzarlo come una fase di installazione iniziale del cluster.
   
   Il comando seguente rimuove qualsiasi file di configurazione del cluster esistenti e Arresta tutti i servizi del cluster. Ciò elimina definitivamente il cluster. Eseguirlo come primo passaggio in un ambiente di pre-produzione. Si noti che 'PC cluster destroy' disabilitato il servizio pacemaker e deve essere riabilitati. Eseguire il comando seguente in tutti i nodi.
   
   >[!WARNING]
   >Il comando Elimina le risorse cluster esistente.

   ```bash
   sudo pcs cluster destroy 
   sudo systemctl enable pacemaker
   ```

1. Creare il cluster. 

   >[!WARNING]
   >A causa di un problema noto che il fornitore clustering è in corso, a partire dal cluster ('PC cluster start') ha esito negativo con il seguente errore. Questo avviene perché il file di log configurati in /etc/corosync/corosync.conf che viene creato quando il comando di installazione del cluster viene eseguito, non è corretto. Per risolvere questo problema, modificare il file di log: /var/log/corosync/corosync.log. In alternativa è possibile creare il file /var/log/cluster/corosync.log.
 
   ```Error
   Job for corosync.service failed because the control process exited with error code. 
   See "systemctl status corosync.service" and "journalctl -xe" for details.
   ```
  
Il comando seguente crea un cluster di tre nodi. Prima di eseguire lo script, sostituire i valori compresi tra `< ... >`. Eseguire il comando seguente nel nodo primario. 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2…> <node3>
   sudo pcs cluster start --all
   ```
   
   >[!NOTE]
   >Se in precedenza è stato configurato un cluster negli stessi nodi, è necessario usare l'opzione '--force' quando si esegue 'pcs cluster setup'. Si noti che ciò equivale all'esecuzione di 'pcs cluster destroy' e il servizio Pacemaker deve essere riabilitato usando 'sudo systemctl enable pacemaker'.


## <a name="configure-fencing-stonith"></a>Configurare fencing (STONITH)

I fornitori di cluster pacemaker richiedono STONITH deve essere abilitata e un dispositivo fencing configurato per l'installazione del cluster supportate. Quando il gestore delle risorse cluster non è possibile determinare lo stato di un nodo o di una risorsa in un nodo, fencing viene utilizzato per visualizzare di nuovo il cluster in uno stato noto. Fencing livello risorse principalmente garantisce che non vi sia alcun danneggiamento dei dati in caso di interruzione tramite la configurazione di una risorsa. È possibile utilizzare fencing livello di risorse, ad esempio, con DRBD (Distributed replicati blocco dispositivo) per contrassegnare il disco in un nodo come obsoleta quando il collegamento di comunicazione si arresta. Fencing livello di nodo garantisce che un nodo non viene eseguito tutte le risorse. In tal caso, reimpostare il nodo e l'implementazione Pacemaker di esso viene chiamato STONITH (che è l'acronimo di "riprendere l'altro nodo nell'intestazione"). Pacemaker supporta una vasta gamma di dispositivi fencing, ad esempio un continuità o gestione delle schede di interfaccia di per i server. Per ulteriori informazioni, vedere [cluster Pacemaker novo](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html) e [Fencing e Stonith](http://clusterlabs.org/doc/crm_fencing.html) 

Poiché il livello del nodo conflitti di configurazione dipende molto dall'ambiente, verrà disabilitata per questa esercitazione (può essere configurato in un secondo momento). Nel nodo primario, eseguire lo script seguente: 

```bash
sudo pcs property set stonith-enabled=false
```

>[!IMPORTANT]
>La disattivazione STONITH è solo a scopo di test. Se si prevede di utilizzare Pacemaker in un ambiente di produzione, pianificare un'implementazione STONITH a seconda dell'ambiente e mantenerla abilitato. Si noti che a questo punto nessun agente fencing per ambienti cloud (Azure inclusi) o Hyper-V. Consequentially, il fornitore del cluster non offre il supporto per i cluster di produzione in esecuzione in questi ambienti. 

## <a name="set-cluster-property-cluster-recheck-interval"></a>Impostare proprietà di cluster del cluster-nuova verifica del-intervallo

`cluster-recheck-interval` indica l'intervallo di polling durante il quale controlla il cluster per la modifica in parametri delle risorse, i vincoli o altre opzioni di cluster. Se una replica diventa inattiva, il cluster tenta di riavviare la replica a un intervallo che è associato il `failure-timeout` valore e il `cluster-recheck-interval` valore. Ad esempio, se `failure-timeout` è impostata su 60 secondi e `cluster-recheck-interval` è impostato su 120 secondi, il riavvio viene eseguito un tentativo a un intervallo che è maggiore di 60 secondi ma inferiore a 120 secondi. È consigliabile impostare timeout errore 60s e intervallo di nuova verifica del cluster su un valore maggiore di 60 secondi. Non è consigliabile impostare l'intervallo di nuova verifica del cluster su un valore basso.

Per aggiornare il valore della proprietà da `2 minutes` eseguire:

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Se si dispone già di una risorsa del gruppo di disponibilità gestita da un cluster Pacemaker, tenere presente che tutte le distribuzioni che usano la versione più recente disponibile Pacemaker pacchetto 1.1.18-11.el7 introducano una modifica del comportamento per il cluster avvia errore-è-irreversibile impostazione quando il relativo valore è false. Questa modifica interessa il flusso di lavoro di failover. Se una replica primaria di cui si verifichi un'interruzione del servizio, il cluster deve eseguire il failover su una delle repliche secondarie disponibili. Al contrario, gli utenti noteranno che il cluster mantiene tenta di avviare la replica primaria non riuscita. Se il database primario non viene portato online (a causa di un'interruzione permanente), failover del cluster mai a un'altra replica secondaria disponibile. Grazie a questa modifica, una configurazione consigliata in precedenza per impostare inizio-errore-è-errore irreversibile non è più valida e l'impostazione deve essere ripristinato il valore predefinito `true`. Inoltre, la risorsa gruppo di disponibilità deve essere aggiornato per includere il `failover-timeout` proprietà. 
>
>Per aggiornare il valore della proprietà da `true` eseguire:
>
>```bash
>sudo pcs property set start-failure-is-fatal=true
>```
>
>Aggiornare le proprietà della risorsa gruppo di disponibilità esistente `failure-timeout` al `60s` eseguire (sostituire `ag1` con il nome della risorsa del gruppo di disponibilità):
>
>```bash
>pcs resource update ag1 meta failure-timeout=60s
>```

## <a name="install-sql-server-resource-agent-for-integration-with-pacemaker"></a>Installare SQL Server agent di risorsa per l'integrazione con Pacemaker

Eseguire i comandi seguenti in tutti i nodi. 

```bash
sudo apt-get install mssql-server-ha
```

## <a name="create-a-sql-server-login-for-pacemaker"></a>Creare un account di accesso di SQL Server per Pacemaker

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>Creare una risorsa del gruppo di disponibilità

Per creare la risorsa del gruppo di disponibilità, utilizzare `pcs resource create` comando e impostare le proprietà della risorsa. Comando seguente crea un `ocf:mssql:ag` master/slave, tipo di risorsa per il gruppo di disponibilità con nome `ag1`. 

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s --master meta notify=true

```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

## <a name="create-virtual-ip-resource"></a>Creare la risorsa IP virtuale

Per creare la risorsa di indirizzo IP virtuale, eseguire il comando seguente in un nodo. Utilizzare un indirizzo IP statico disponibile dalla rete. Prima di eseguire lo script, sostituire i valori compresi tra `< ... >` con un indirizzo IP valido.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Nessun nome server virtuale è equivalente al Pacemaker. Per utilizzare una stringa di connessione che punta al nome di un server di stringa e non usare l'indirizzo IP, registrare l'indirizzo risorsa IP e nome del server virtuale desiderato nel DNS. Per le configurazioni di ripristino di emergenza, registrare il nome del server virtuale desiderato e l'indirizzo IP con i server DNS primario sia del sito di ripristino di emergenza.

## <a name="add-colocation-constraint"></a>Aggiungere il vincolo di percorso condiviso

Quasi ogni decisione in un cluster Pacemaker, ad esempio la scelta in cui deve essere eseguita una risorsa, viene eseguita confrontando i punteggi. I punteggi vengono calcolati per ogni risorsa e la gestione delle risorse cluster sceglie il nodo con il punteggio più alto per una particolare risorsa. (Se un nodo ha un punteggio negativo per una risorsa, la risorsa non è possibile eseguire su tale nodo.) Utilizzare i vincoli per configurare le decisioni del cluster. I vincoli hanno un punteggio. Se un vincolo ha un punteggio inferiore a infinito, è solo un'indicazione. Un punteggio di infinito indica che è obbligatorio. Per garantire che la replica primaria e la risorsa indirizzo ip virtuale nello stesso host, definire un vincolo di percorso condiviso con un punteggio di infinito. Per aggiungere il vincolo di percorso condiviso, eseguire il comando seguente in un nodo. 

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>Aggiungi vincolo di ordinamento

Il vincolo di condivisione del percorso include un vincolo di ordinamento implicito. Sposta la risorsa IP virtuale prima di spostare la risorsa del gruppo di disponibilità. Per impostazione predefinita è la sequenza di eventi:

1. Problemi relativi all'utente `pcs resource move` al gruppo di disponibilità primario da node1 a node2.
1. La risorsa IP virtuale viene arrestata nel nodo 1.
1. La risorsa IP virtuale viene avviato sul nodo 2.

   >[!NOTE]
   >A questo punto, l'indirizzo IP temporaneamente punti a node2 mentre node2 è ancora un failover precedente secondario. 
   
1. Il gruppo di disponibilità primario sul nodo 1 viene abbassato a quello secondario.
1. Il gruppo di disponibilità secondario sul nodo 2 viene promossa a primaria. 

Per evitare temporaneamente che puntano al nodo con il database secondario precedente failover l'indirizzo IP, aggiungere un vincolo di ordinamento. 

Per aggiungere un vincolo di ordinamento, eseguire il comando seguente in un nodo:

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>Dopo la configurazione del cluster e aggiungere il gruppo di disponibilità come risorsa cluster, è possibile usare Transact-SQL per il failover delle risorse del gruppo di disponibilità. Risorse del cluster di SQL Server in Linux non sono collegate come strettamente con il sistema operativo come se fossero in un Windows Server Failover Cluster (WSFC). Servizio SQL Server non riconosce la presenza del cluster. Tutte le orchestrazioni viene eseguita tramite gli strumenti di gestione di cluster. RHEL o Ubuntu utilizzare `pcs`. 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Passaggi successivi

[Utilizzare il gruppo di disponibilità elevata](sql-server-linux-availability-group-failover-ha.md)

