---
title: Configurazione di cluster condiviso Red Hat Enterprise Linux per SQL Server | Documenti Microsoft
description: "Implementare la disponibilità elevata mediante la configurazione cluster disco condiviso Red Hat Enterprise Linux per SQL Server."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.workload: On Demand
ms.openlocfilehash: ce2427d4defca8640d93ea25919fe805ac7c6133
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Configurare il cluster di dischi condivisi Red Hat Enterprise Linux per SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Questa guida fornisce istruzioni su come creare un cluster di dischi condivisi a due nodi per SQL Server su Red Hat Enterprise Linux. Il livello di clustering si basa su Red Hat Enterprise Linux (RHEL) [componente aggiuntivo a disponibilità elevata](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) compilato in cima [Pacemaker](http://clusterlabs.org/). L'istanza di SQL Server è attivo in un nodo o l'altro.

> [!NOTE] 
> Accesso alla documentazione e componente aggiuntivo Red Hat a disponibilità elevata richiede una sottoscrizione. 

Come illustrato nella figura seguente viene illustrata l'archiviazione è presentata a due server. I componenti di clustering - Corosync e Pacemaker - coordinano le comunicazioni e gestione delle risorse. Uno dei server con la connessione attiva per le risorse di archiviazione e SQL Server. Quando il Pacemaker rileva un errore i componenti di clustering gestiscono lo spostamento di risorse a altro nodo.  

![Red Hat Enterprise Linux 7 condiviso del Cluster SQL disco](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Per ulteriori informazioni su configurazione cluster, le opzioni di agenti di risorsa e la gestione, visitare [la documentazione di riferimento RHEL](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).


> [!NOTE] 
> Integrazione di SQL Server con Pacemaker a questo punto, non è accoppiata come con WSFC in Windows. All'interno di SQL, non è possibile sapere sulla presenza del cluster, tutte le orchestrazioni non rientra e il servizio viene controllato come istanza autonoma da Pacemaker. Inoltre, ad esempio, sys.dm os_cluster_properties e Sys.dm os_cluster_nodes DMV cluster non sarà alcun record.
Per utilizzare una stringa di connessione che punta al nome di un server di stringa e non usa l'indirizzo IP, sarà necessario registrare in un server DNS l'indirizzo IP utilizzato per creare la risorsa IP virtuale (come illustrato di seguito) con il nome del server selezionato.

Nelle sezioni seguenti viene illustrata la procedura per configurare una soluzione di cluster di failover. 

## <a name="prerequisites"></a>Prerequisites

Per completare lo scenario end-to-end seguente devono essere presenti due macchine per distribuire il cluster a due nodi e un altro server per configurare il server NFS. Passaggi seguenti viene descritto come questi server verranno configurati.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Installare e configurare il sistema operativo in ogni nodo del cluster

Il primo passaggio consiste nel configurare il sistema operativo nei nodi del cluster. Per questa procedura dettagliata, è possibile utilizzare RHEL con una sottoscrizione valida per il componente aggiuntivo a disponibilità elevata. 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Installare e configurare SQL Server in ogni nodo del cluster

1. Installare e configurare SQL Server in entrambi i nodi.  Per informazioni dettagliate vedere [installazione di SQL Server in Linux](sql-server-linux-setup.md).

1. Specificare un nodo primario e l'altro come secondario, ai fini di configurazione. Utilizzare questi termini per le operazioni seguenti in questa Guida.  

1. Nel nodo secondario, arrestare e disabilitare il Server SQL.

   Nell'esempio seguente arresta e disattiva SQL Server: 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> In fase di installazione, viene generato per l'istanza di SQL Server e inserito in una chiave Master del Server `/var/opt/mssql/secrets/machine-key`. In Linux, SQL Server viene sempre eseguito come un account locale denominato mssql. Poiché si tratta di un account locale, l'identità non è condivise tra i nodi. Pertanto, è necessario copiare la chiave di crittografia dal nodo primario a ogni nodo secondario in modo che ogni account locale mssql possono accedervi per decrittografare la chiave Master del Server. 

1. Nel nodo primario, creare un account di accesso SQL server per Pacemaker e concedere l'autorizzazione di accesso per l'esecuzione `sp_server_diagnostics`. Pacemaker utilizzerà questo account per verificare quale sia il nodo è in esecuzione SQL Server. 

   ```bash
   sudo systemctl start mssql-server
   ```

   Connettersi a SQL Server `master` con l'account sa di database ed eseguire le operazioni seguenti:

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   In alternativa, è possibile impostare le autorizzazioni a un livello più granulare. Richiede l'account di accesso Pacemaker `VIEW SERVER STATE` per query sullo stato di integrità con sp_server_diagnostics, `setupadmin` e `ALTER ANY LINKED SERVER` per aggiornare il nome dell'istanza FCI con il nome della risorsa eseguendo sp_dropserver e sp_addserver. 

1. Nel nodo primario, arrestare e disabilitare il Server SQL. 

1. Configurare il file hosts per ogni nodo del cluster. Il file di host deve includere l'indirizzo IP e nome di ogni nodo del cluster. 

    Controllare l'indirizzo IP per ogni nodo. Lo script seguente viene illustrato l'indirizzo IP del nodo corrente. 

   ```bash
   sudo ip addr show
   ```

   Impostare il nome del computer in ogni nodo. Assegnare a ogni nodo un nome univoco che è di 15 caratteri o meno. Impostare il nome del computer, aggiungerlo al `/etc/hosts`. Lo script seguente consente di modificare `/etc/hosts` con `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```
   Nell'esempio seguente `/etc/hosts` aggiunte due nodi denominati `sqlfcivm1` e `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

Nella sezione successiva verrà configurare l'archiviazione condivisa e spostare i file di database che l'archiviazione. 

## <a name="configure-shared-storage-and-move-database-files"></a>Configurare l'archiviazione condivisa e spostare i file di database 

Sono disponibili un'ampia gamma di soluzioni per fornire l'archiviazione condivisa. Questa procedura dettagliata viene illustrata la configurazione di archiviazione condivisa con NFS. Si consiglia di seguire le procedure consigliate e utilizzano l'autenticazione Kerberos per la protezione di NFS (è possibile trovare un esempio di seguito: https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/). 

>[!Warning]
>Se non si protegge NFS, chiunque può accedere alla rete e lo spoofing l'indirizzo IP di un nodo SQL sarà in grado di accedere ai file di dati. Come sempre, assicurarsi di minaccia del modello del sistema prima di utilizzarlo nell'ambiente di produzione. Un'altra opzione di archiviazione consiste nell'utilizzare una condivisione file SMB.

### <a name="configure-shared-storage-with-nfs"></a>Configurare l'archiviazione condivisa con NFS

> [!IMPORTANT] 
> Hosting dei file di database in un server NFS con versione < 4 non è supportata in questa versione. Include l'utilizzo di NFS per disco condiviso clustering di failover e database nelle istanze non cluster. Stiamo lavorando sull'abilitazione di altre versioni del server NFS nelle prossime versioni. 

Il Server NFS eseguire le operazioni seguenti:

1. Installare `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Abilitare e avviare`rpcbind`

   ```bash
   sudo systemctl enable rpcbind && sudo systemctl start rpcbind
   ```

1. Abilitare e avviare`nfs-server`
 
   ```bash
   sudo systemctl enable nfs-server && sudo systemctl start nfs-server
   ```
 
1.  Modifica `/etc/exports` per esportare la directory in cui si desidera condividere. È necessario 1 riga per ogni condivisione desiderata. Ad esempio 

   ```bash
   /mnt/nfs  10.8.8.0/24(rw,sync,no_subtree_check,no_root_squash)
   ```

1. Esportare le condivisioni

   ```bash
   sudo exportfs -rav
   ```

1. Verificare che i percorsi sono condivisi/esportato, eseguiti dal server NFS

   ```bash
   sudo showmount -e
   ```

1. Aggiungere l'eccezione in SELinux

   ```bash
   sudo setsebool -P nfs_export_all_rw 1
   ```
   
1. Aprire il firewall, il server.

   ```bash 
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Configurare tutti i nodi del cluster per la connessione alla risorsa di archiviazione condivise NFS

Eseguire i passaggi seguenti in tutti i nodi del cluster.

1.  Installare `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Aprire il firewall nel client e server NFS

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

1. Verificare che è possibile visualizzare le condivisioni NFS nei computer client

   ```bash
   sudo showmount -e <IP OF NFS SERVER>
   ```

1. Ripetere questi passaggi in tutti i nodi del cluster.

Per ulteriori informazioni sull'utilizzo di NFS, vedere le risorse seguenti:

* [NFS Server e firewalld | Scambio dello stack](http://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [Montare un Volume NFS | Manuale dell'amministratore di rete Linux](http://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [Configurazione del server NFS](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-nfs-server-export.html)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>Montare directory dei file di database in modo da puntare all'archiviazione condivisa

1.  **Nel nodo primario**, salvare i file di database in un percorso temporaneo. Lo script seguente, crea una nuova directory temporanea, copia i file di database nella nuova directory e rimuove i file di database precedente. Come SQL Server viene eseguito come utente locale mssql, è necessario assicurarsi che dopo il trasferimento di dati per la condivisione montata, utente locale ha accesso in lettura-scrittura alla condivisione. 

   ``` 
   $ sudo su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1.  In tutti i nodi del cluster modificare `/etc/fstab` file da includere il comando di montaggio.  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   Lo script seguente viene illustrato un esempio della modifica.  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>Se si utilizza una risorsa del File System (FS), come indicato di seguito, non è necessario per mantenere il comando di montaggio in /etc/fstab. Pacemaker si occuperà di montare la cartella quando avvia la risorsa di ADFS in cluster. Con l'aiuto di geofencing, si verifica un schermo ADFS non è montato due volte. 

1.  Eseguire `mount -a` comando per il sistema aggiornare i percorsi montati.  

1.  Copiare i file di database e di log che è stato salvato in `/var/opt/mssql/tmp` alla condivisione appena montata `/var/opt/mssql/data`. Questo deve essere eseguita solo **nel nodo primario**. Assicurarsi che si assegnano autorizzazioni di lettura/scrittura all'utente locale 'mssql'.

   ``` 
   $ sudo chown mssql /var/opt/mssql/data
   $ sudo chgrp mssql /var/opt/mssql/data
   $ sudo su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1.  Verificare che SQL Server venga avviato correttamente con il nuovo percorso del file. Eseguire questa operazione in ogni nodo. A questo punto, solo un nodo deve eseguire SQL Server alla volta. Non possono entrambi eseguiti nello stesso momento poiché entrambe tenteranno di accedere ai file di dati contemporaneamente (per evitare accidentalmente l'avvio di SQL Server in entrambi i nodi, utilizzare una risorsa cluster di File System per assicurarsi che la condivisione non è montata due volte per i diversi nodi). I seguenti comandi di avvio di SQL Server, controllano lo stato e quindi arrestare SQL Server.
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
A questo punto, entrambe le istanze di SQL Server sono configurate per eseguire con i file di database all'archiviazione condivisa. Il passaggio successivo consiste nel configurare SQL Server per Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installare e configurare Pacemaker su ogni nodo del cluster


2. In entrambi i nodi del cluster creare un file per archiviare nome utente e password di SQL Server per l'accesso a Pacemaker. Il comando seguente crea e popola questo file:

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   echo '<loginName>' | sudo tee -a /var/opt/mssql/secrets/passwd
   echo '<loginPassword>' | sudo tee -a /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. In entrambi i nodi del cluster aprire le porte del firewall di Pacemaker. Per aprire queste porte con `firewalld`, eseguire il comando seguente:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Se si sta usando un altro firewall che non ha una configurazione a disponibilità elevata predefinita, è necessario aprire le porte seguenti per consentire a Pacemaker di comunicare con altri nodi del cluster
   >
   > * TCP: porte 2224, 3121, 21064
   > * UDP: porta 5405

1. Installare i pacchetti Pacemaker in ogni nodo.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

   

2. Impostare la password per l'utente predefinito creato durante l'installazione dei pacchetti Corosync e Pacemaker. Usare la stessa password in entrambi i nodi. 

   ```bash
   sudo passwd hacluster
   ```

   

3. Abilitare e avviare il servizio `pcsd` e Pacemaker. In questo modo, i nodi potranno unirsi nuovamente in join con il cluster dopo il riavvio. Eseguire il comando seguente in entrambi i nodi.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Installare l'agente delle risorse FCI per SQL Server. Eseguire i comandi seguenti in entrambi i nodi. 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="create-the-cluster"></a>Creare il cluster 

1. In uno dei nodi, creare il cluster.

   ```bash
   sudo pcs cluster auth <nodeName1 nodeName2 …> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 …>
   sudo pcs cluster start --all
   ```

   > RHEL a disponibilità elevata include conflitti agenti per KVM e VMWare. Fencing deve essere disabilitata in tutti gli altri hypervisor. Non è consigliabile disabilitare gli agenti fencing negli ambienti di produzione. A partire da intervallo di tempo, non sono agenti fencing per gli ambienti Hyper-v o il cloud. Se si esegue una di queste configurazioni, è necessario disabilitare fencing. \**Questa operazione è sconsigliata in un sistema di produzione.**

   Il comando seguente disabilita gli agenti di geofencing.

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. Configurare le risorse del cluster per SQL Server, File System e le risorse IP virtuali e il push della configurazione per il cluster. È necessario che le informazioni seguenti:

   - **Nome di risorsa di SQL Server**: un nome per la risorsa cluster di SQL Server. 
   - **Valore di timeout**: il valore di timeout è la quantità di tempo di attesa cluster mentre un una risorsa viene portata online. Per SQL Server, questo è il tempo che si prevede di SQL Server per portare il `master` database online.  
   - **Nome risorsa IP mobile**: un nome per la risorsa di indirizzo IP virtuale.
   - **Indirizzo IP**: l'indirizzo IP che i client utilizzeranno per connettersi all'istanza del cluster di SQL Server. 
   - **Il nome di risorsa sistema**: un nome per la risorsa del File System.
   - **dispositivo**: NFS il percorso di condivisione.
   - **dispositivo**: il percorso locale che è attivato per la condivisione
   - **fsType**: il tipo di condivisione File (ad esempio nfs)

   Aggiornare i valori dallo script seguente per l'ambiente. Eseguire in un nodo per configurare e avviare il servizio cluster.  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci op defaults timeout=<timeout_in_seconds>
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   Ad esempio, lo script seguente crea una risorsa cluster di SQL Server denominata `mssqlha`e una risorsa IP mobile con l'indirizzo IP `10.0.0.99`. Inoltre, crea una risorsa del file System e aggiunge i vincoli in modo che tutte le risorse sono installate nello stesso nodo come risorsa SQL. 

   ```bash
   sudo pcs cluster cib cfg
   sudo pcs -f cfg resource create mssqlha ocf:mssql:fci op defaults timeout=60s
   sudo pcs -f cfg resource create virtualip ocf:heartbeat:IPaddr2 ip=10.0.0.99
   sudo pcs -f cfg resource create fs Filesystem device="10.8.8.0:/mnt/nfs" directory="/var/opt/mssql/data" fstype="nfs"
   sudo pcs -f cfg constraint colocation add virtualip mssqlha
   sudo pcs -f cfg constraint colocation add fs mssqlha
   sudo pcs cluster cib-push cfg
   ```

   Dopo la configurazione viene inserita, SQL Server viene avviato in un nodo. 

3. Verificare che SQL Server sia avviato. 

   ```bash
   sudo pcs status 
   ```

   L'esempi seguenti viene mostrato i risultati ottenuti quando Pacemaker è stato avviato un'istanza cluster di SQL Server. 

   ```
   fs     (ocf::heartbeat:Filesystem):    Started sqlfcivm1
   virtualip     (ocf::heartbeat:IPaddr2):      Started sqlfcivm1
   mssqlha  (ocf::mssql:fci): Started sqlfcivm1
   
   PCSD Status:
    slqfcivm1: Online
    sqlfcivm2: Online
   
   Daemon Status:
    corosync: active/disabled
    pacemaker: active/enabled
    pcsd: active/enabled
   ```

## <a name="additional-resources"></a>Risorse aggiuntive

* [Cluster da zero](http://clusterlabs.org/doc/Cluster_from_Scratch.pdf) Guida Pacemaker

## <a name="next-steps"></a>Passaggi successivi

[Funzionamento di SQL Server in cluster dei dischi condivisi Red Hat Enterprise Linux](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
