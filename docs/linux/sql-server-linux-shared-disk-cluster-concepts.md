---
title: Le istanze del Cluster di failover, SQL Server in Linux | Documenti Microsoft
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: a9e8964b16eff5da35ef3abac6f493afc7615903
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="failover-cluster-instances---sql-server-on-linux"></a>Istanze del Cluster di failover, SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo illustra i concetti relativi a SQL Server istanze cluster di failover (FCI) in Linux. 

Per creare una FCI di SQL Server in Linux, vedere [configurazione di FCI di SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure.md)

## <a name="the-clustering-layer"></a>Il livello di Clustering

* In RHEL, il livello di clustering si basa su Red Hat Enterprise Linux (RHEL) [componente aggiuntivo a disponibilità elevata](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf). 

    > [!NOTE] 
    > Accesso alla documentazione e componente aggiuntivo Red Hat a disponibilità elevata richiede una sottoscrizione. 

* In SLES, il livello di clustering si basa su SUSE Linux Enterprise [estensione a disponibilità elevata (Georgiano)](https://www.suse.com/products/highavailability).

    Per informazioni sulla configurazione del cluster, le opzioni di agente di risorse, gestione, procedure consigliate e indicazioni, vedere [SUSE Linux Enterprise ad alta disponibilità estensione 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

Sia il componente RHEL a disponibilità elevata e il HAE SUSE vengono compilati su [Pacemaker](http://clusterlabs.org/).

Come illustrato nella figura seguente, l'archiviazione è presentata a due server. I componenti di clustering - Corosync e Pacemaker - coordinano le comunicazioni e gestione delle risorse. Uno dei server con la connessione attiva per le risorse di archiviazione e SQL Server. Quando il Pacemaker rileva un errore i componenti di clustering gestiscono lo spostamento di risorse a altro nodo.  

![Red Hat Enterprise Linux 7 condiviso del Cluster SQL disco](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 


> [!NOTE]
> A questo punto, integrazione di SQL Server con Pacemaker in Linux non è accoppiata come con WSFC in Windows. All'interno di SQL, non è possibile sapere sulla presenza del cluster, tutte le orchestrazioni non rientra e il servizio viene controllato come istanza autonoma da Pacemaker. Inoltre, il nome di rete virtuale è specifico di WSFC, è disponibile un equivalente dello stesso in Pacemaker. È previsto che @@servername e Sys. Servers per restituire il nome del nodo, mentre lo Sys.dm os_cluster_nodes DMV di cluster e Sys.dm os_cluster_properties non sarà alcun record. Per utilizzare una stringa di connessione che punta al nome di un server di stringa e non usa l'indirizzo IP, sarà necessario registrare i server DNS l'indirizzo IP utilizzato per creare la risorsa IP virtuale (come descritto nelle sezioni seguenti) con il nome di server selezionato.

## <a name="number-of-instances-and-nodes"></a>Numero di istanze e nodi

Una differenza principale con SQL Server in Linux è che può essere presente solo un'installazione di SQL Server per server Linux. L'installazione viene chiamata un'istanza. Ciò significa che Windows Server che supporta fino a 25 FCI per cluster di failover di Windows Server (WSFC), a differenza di un'istanza cluster di failover basati su Linux avrà solo una singola istanza. Questa istanza è anche un'istanza predefinita; non è previsto di un'istanza denominata su Linux. 

Un cluster Pacemaker può avere solo un massimo di 16 nodi quando è coinvolto Corosync, pertanto una singola istanza del cluster di failover può estendersi fino a 16 server. Un'istanza FCI implementata con l'edizione Standard di SQL Server supporta fino a due nodi di un cluster, anche se il cluster Pacemaker è il numero massimo di 16 nodi.

In SQL Server FCI, è attiva su un nodo o l'altra istanza di SQL Server.

## <a name="ip-address-and-name"></a>Nome e indirizzo IP
In un cluster Linux Pacemaker, ogni FCI di SQL Server è necessario il proprio indirizzo IP univoco e nome. Se la configurazione di FCI si estende su più subnet, un indirizzo IP sarà obbligatorio per ogni subnet. Il nome univoco e gli indirizzi IP vengono utilizzati per accedere l'istanza FCI, in modo che le applicazioni e gli utenti finali non è necessario sapere in quale server del cluster Pacemaker sottostante.

Il nome dell'istanza FCI in DNS deve essere identico al nome della risorsa istanza cluster di failover che viene creato nel cluster Pacemaker.
Il nome e l'indirizzo IP deve essere registrati in DNS.

## <a name="shared-storage"></a>Archiviazione condivisa
Tutte le istanze FCI, siano essi in Linux o Windows Server, richiedono una qualche forma di archiviazione condivisa. Questa risorsa di archiviazione viene visualizzato in tutti i server che possono ospitare eventualmente l'infrastruttura di classificazione file, ma solo un singolo server può utilizzare lo spazio di archiviazione per l'istanza FCI in qualsiasi momento. Le opzioni disponibili per l'archiviazione condivisa in Linux sono:

- iSCSI
- Network File System (NFS)
- Server Message Block (SMB) in Windows Server, sono disponibili opzioni leggermente diverse. Un'opzione non è attualmente supportata per FCI basati su Linux è la possibilità di utilizzare un disco locale per il nodo per il database TempDB, ovvero l'area di lavoro temporanea di SQL Server.

In una configurazione che si estende su più percorsi, il contenuto archiviato in un data center deve essere sincronizzato con l'altro. In caso di failover, l'istanza FCI sarà in grado di portare in linea e viene visualizzato lo spazio di archiviazione siano gli stessi. Raggiungere questo obiettivo richiederà un metodo esterno per la replica di archiviazione, l'operazione venga eseguita tramite l'hardware di archiviazione sottostante o un'utilità basata su software. 

>[!NOTE]
>Per SQL Server 2017, le distribuzioni basate su Linux utilizzando dischi presentati direttamente a un server di questo tipo devono essere formattate con XFS o EXT4. Altri sistemi di file non sono attualmente supportati. Tutte le modifiche si rifletteranno qui.

Il processo per la presentazione di spazio di archiviazione condiviso è la stessa per i diversi metodi supportati:

- Configurare l'archiviazione condivisa
- Installare lo spazio di archiviazione come cartella per i server da utilizzare come nodi del cluster Pacemaker per l'istanza FCI
- Se necessario, spostare i database di sistema di SQL Server per l'archiviazione condivisa
- Verificarne il funzionamento di SQL Server da ogni server collegato per l'archiviazione condivisa

La principale differenza con SQL Server in Linux è che sebbene sia possibile configurare il percorso di file predefinito dati e di log dell'utente, i database di sistema devono essere sempre presente in `/var/opt/mssql/data`. In Windows Server, è la possibilità di spostare i database di sistema, incluso TempDB. Ciò viene riprodotto in archiviazione condivisa come è configurato per un'istanza FCI.

I percorsi predefiniti per i database di sistema non possono essere modificati utilizzando il `mssql-conf` utilità. Per informazioni su come modificare le impostazioni predefinite, [modificare il percorso di directory dati o di log predefinito](sql-server-linux-configure-mssql-conf.md#datadir). È anche possibile archiviare i dati di SQL Server e transazioni in altre posizioni, purché dispongano della protezione, anche se non è un percorso predefinito. il percorso dovrebbe essere indicato.

Gli argomenti seguenti illustrano come configurare i tipi di archiviazione supportati per Linux base istanza cluster di failover di SQL Server:

- [Configurare l'istanza del cluster di failover SQL Server in Linux - iSCSI:](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Configurare i cluster di failover - NFS - SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Configurazione di cluster di failover - SMB - SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)
