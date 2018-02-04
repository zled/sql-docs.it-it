---
title: 'Aggiornato: SQL Server in Linux docs | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per Microsoft SQL Server in Linux.
services: na
documentationcenter: 
author: MightyPen
manager: craigg
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: d477af0c4c7027892d4ade8e586c9a9b908a05ea
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nuovi e recentemente aggiornato: SQL Server in Linux documenti



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **Microsoft SQL Server in Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Eseguire il 2017 di SQL Server nel cloud](quickstart-install-connect-clouds.md)
2. [Repository di modifica dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md)
3. [Procedure consigliate e linee guida di configurazione per SQL Server 2017 su Linux](sql-server-linux-performance-best-practices.md)
4. [Istanze del Cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-concepts.md)
5. [Configurare l'istanza del cluster di failover SQL Server in Linux - iSCSI:](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
6. [Configurare i cluster di failover - NFS - SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
7. [Configurazione di cluster di failover - SMB - SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)
8. [Utilizzare l'istanza del cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-operate.md)
9. [Limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md)
10. [Ripristinare un database di SQL Server in un contenitore Linux Docker](tutorial-restore-backup-in-sql-server-container.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Eseguire l'immagine di SQL Server 2017 contenitore con Docker](#TitleNum_1)
2. [Configura gruppo di disponibilità AlwaysOn per SQL Server in Linux](#TitleNum_2)
3. [Elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](#TitleNum_3)
4. [Configurare le immagini contenitore di SQL Server 2017 in Docker](#TitleNum_4)
5. [Crittografia delle connessioni a SQL Server in Linux](#TitleNum_5)
6. [Creare ed eseguire processi di SQL Server Agent in Linux](#TitleNum_6)
7. [Guida all'installazione per SQL Server in Linux](#TitleNum_7)
8. [Configurare l'istanza del cluster di failover, SQL Server in Linux (RHEL)](#TitleNum_8)
9. [Risolvere i problemi relativi a SQL Server in Linux](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-run-the-sql-server-2017-container-image-with-dockerquickstart-install-connect-dockermd"></a>1. &nbsp;[Eseguire 2017 di SQL Server immagine contenitore con Docker](quickstart-install-connect-docker.md)

*Aggiornamento: 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 261.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2aaf953c2f1fb675b1304186108fbef1eebf6f8f f7cd42bb320a8892a5ec63ce999186438097636a  (PR=4150  ,  Filename=quickstart-install-connect-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**Rimuovere il contenitore**


Se si desidera rimuovere il contenitore di SQL Server utilizzato in questa esercitazione, eseguire i comandi seguenti:

```
sudo docker stop sql1
sudo docker rm sql1
```

```
docker stop sql1
docker rm sql1
```

> [!WARNING]
> L'arresto e rimozione di un contenitore in modo permanente Elimina i dati di SQL Server nel contenitore. Se si desidera conservare i dati, [creare e copiare un file di backup fuori il container--tutorial-restore-backup-in-sql-server-container.md) oppure utilizzare una [contenitore persistenza dei dati technique--sql-server-linux-configure-docker.md#persist).




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-always-on-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-configure-hamd"></a>2. &nbsp;[Configurare sempre nel gruppo di disponibilità per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 129.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c7e6bc862e5b062a855918efbeee5fe748b7236 6900c9a30ce04ce54e7aaa270ef7d276c18f9afd  (PR=4150  ,  Filename=sql-server-linux-availability-group-configure-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



- Creare il gruppo di disponibilità con due repliche sincrone e una replica di configurazione:

   >[!IMPORTANT]
   >Questa architettura consente a qualsiasi edizione di SQL Server per ospitare la replica di terza. Ad esempio, la terza replica può essere ospitata in SQL Server Enterprise Edition. In Enterprise Edition, è il tipo di endpoint valido solo `WITNESS`.

```sql
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
       N'**<node1>**' WITH (
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node2>**' WITH (
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node3>**' WITH (
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**',
          AVAILABILITY_MODE = CONFIGURATION_ONLY
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-high-availability-and-data-protection-for-availability-group-configurationssql-server-linux-availability-group-hamd"></a>3. &nbsp;[Elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità](sql-server-linux-availability-group-ha.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 106.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e6bee794ce19f1ed62298b4a0cce7207550f1595 b64726cd6e91721850721786d26c170d59fc320a  (PR=4150  ,  Filename=sql-server-linux-availability-group-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Il valore predefinito per `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` è 0. Nella tabella seguente descrive il comportamento di disponibilità.

| |Disponibilità elevata & </br> protezione dei dati | Protezione dei dati
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|1
|Interruzione primaria | Failover automatico. Nuovo database primario è R / w. | Failover automatico. Nuovo database primario non è disponibile per le transazioni utente.
|Interruzione di replica secondaria | Filegroup primario è L/S, in esecuzione esposto alla perdita di dati (se primario ha esito negativo e non può essere ripristinato). Nessun failover automatico se primario non riesce. | Database primario non è disponibile per le transazioni utente. Nessuna replica per eseguire il failover se primario non riesce.
|Interruzione di replica sola configurazione | Primario è R / w. Nessun failover automatico se primario non riesce. | Primario è R / w. Nessun failover automatico se primario non riesce.
|Database secondario sincrono + configurazione solo un'interruzione di replica| Database primario non è disponibile per le transazioni utente. Nessun failover automatico. | Database primario non è disponibile per le transazioni utente. Per eseguire il failover se non vi sono repliche primarie non riuscirà.
<sup>*</sup>Impostazione predefinita

>[!NOTE]
>L'istanza di SQL Server che ospita la replica solo configurazione può ospitare anche altri database. Può anche fare parte di un database di configurazione solo per più di un gruppo di disponibilità.

**Requisiti**


* Tutte le repliche di un gruppo di disponibilità con una replica di sola configurazione devono essere SQL Server 2017 CU 1 o versione successiva.
* Qualsiasi edizione di SQL Server può ospitare una replica di sola configurazione, incluso SQL Server Express.
* Il gruppo di disponibilità richiede almeno una replica secondaria, oltre alla replica primaria.
* Il numero massimo di repliche per ogni istanza di SQL Server non vengono contano sole repliche di configurazione. SQL Server standard edition consente fino a tre repliche, SQL Server Enterprise Edition consente un massimo di 9.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>4. &nbsp;[Configurare SQL Server 2017 le immagini contenitore Docker](sql-server-linux-configure-docker.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3) | [Avanti](#TitleNum_5))

<!-- Source markdown line 34.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c759fb88ae8d654414202f28c5fc58dfd02581bf fd270118f2f4608fceaf563fc143951b41097bdb  (PR=4150  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Questa sezione di configurazione fornisce scenari di utilizzo aggiuntive nelle sezioni seguenti.

**<a id="production"></a>Eseguire le immagini contenitore di produzione**


Guida introduttiva nella sezione precedente viene eseguita l'edizione Developer gratuita di SQL Server dall'Hub Docker. La maggior parte delle informazioni si applica comunque Se si desidera eseguire le immagini contenitore, ad esempio le edizioni Enterprise, Standard o Web di produzione. Tuttavia, esistono alcune differenze descritte di seguito.

- È possibile utilizzare solo SQL Server in un ambiente di produzione, se si dispone di una licenza valida. È possibile ottenere una licenza di produzione SQL Server Express gratuita [qui](https://go.microsoft.com/fwlink/?linkid=857693). Licenze di SQL Server Standard ed Enterprise Edition sono disponibili tramite [Microsoft Volume Licensing](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx).

- Le immagini contenitore di SQL Server di produzione devono essere recuperate da [Docker archivio](https://store.docker.com). Se si dispone già di uno, creare un account nell'archivio di Docker.

- L'immagine contenitore sviluppatore nell'archivio di Docker può essere configurato per l'esecuzione anche le edizioni di produzione. Utilizzare la procedura seguente per eseguire le edizioni di produzione:

   1. Innanzitutto, effettuare l'accesso all'id di docker dalla riga di comando.

```
      docker login
```

   1. Successivamente, è necessario ottenere lo sviluppatore gratuito immagine contenitore nell'archivio di Docker. Passare a [https://store.docker.com/images/mssql-server-linux](https://store.docker.com/images/mssql-server-linux), fare clic su **procedere con l'estrazione**e seguire le istruzioni.

   1. Esaminare i requisiti e di eseguire le procedure della [Guida introduttiva - avvio rapido-installazione-connessione-docker.md). Tuttavia, vi sono due differenze. È necessario effettuare il pull dell'immagine **archivio/microsoft/mssql-server-linux:\<-nome del tag\>**  dall'archivio di Docker. Ed è necessario specificare l'edizione di produzione con la **MSSQL_PID** variabile di ambiente. Nell'esempio seguente viene illustrato come eseguire l'ultima immagine contenitore 2017 di SQL Server per l'edizione Enterprise:



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-encrypting-connections-to-sql-server-on-linuxsql-server-linux-encrypted-connectionsmd"></a>5. &nbsp;[Crittografia delle connessioni a SQL Server in Linux](sql-server-linux-encrypted-connections.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_4) | [Avanti](#TitleNum_6))

<!-- Source markdown line 45.  ms.author= meetb;rickbyh.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e3187866df060903e30000d60d673edad46d210 bcb1f2771e6c29b535a30b9f23ac296954509187  (PR=4150  ,  Filename=sql-server-linux-encrypted-connections.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



        sudo chown mssql:mssql mssql.pem mssql.key
        sudo chmod 600 mssql.pem mssql.key
        sudo mv mssql.pem /etc/ssl/certs/
        sudo mv mssql.key /etc/ssl/private/

- **Configurare SQL Server**

        systemctl stop mssql-server
        cat /var/opt/mssql/mssql.conf
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0

- **Registrare il certificato nel computer client (Windows, Linux o Mac OS)**

    -   Se si usa un certificato CA firmato è necessario copiare il certificato di autorità di certificazione (CA) anziché il certificato utente nel computer client.
    -   Se si utilizza il certificato autofirmato appena copiare il file PEM nelle cartelle seguenti rispettive al distribuzione ed eseguire i comandi per abilitarli

        - **Windows**: Importa il file con estensione PEM come un certificato in utente corrente -> attendibile l'autorità di certificazione radice -> certificati
        - **macOS**:

-   **Esempi di stringhe di connessione**

    - **..!NCLUDE-NotShown--ssmanstudiofull-md--../includes/ssmanstudiofull-md.md)]** ![SSMS connection dialog--media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "SSMS connection dialog")



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-create-and-run-sql-server-agent-jobs-on-linuxsql-server-linux-run-sql-server-agent-jobmd"></a>6. &nbsp;[Creazione e l'esecuzione dei processi di SQL Server Agent in Linux](sql-server-linux-run-sql-server-agent-job.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_5) | [Avanti](#TitleNum_7))

<!-- Source markdown line 35.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1598129bb5f98434435d8ad02336a9adf76c7870 6fe3fe7df3a60dbac31f1df59aac9860d293421a  (PR=4150  ,  Filename=sql-server-linux-run-sql-server-agent-job.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Per completare questa esercitazione, sono necessari i seguenti prerequisiti:

* Computer Linux con i seguenti prerequisiti:
  * SQL Server 2017 ([RHEL--quickstart-install-connect-red-hat.md), [SLES - avvio rapido-installazione-connessione-suse.md) o [Ubuntu - avvio rapido-installazione-connessione-ubuntu.md)) con gli strumenti da riga di comando.

I prerequisiti seguenti sono facoltativi:

* Computer Windows con SQL Server Management Studio:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) per passaggi facoltativi di SQL Server Management Studio.

**Installare SQL Server Agent**


Per utilizzare SQL Server Agent in Linux, è necessario installare il **mssql-server agent** pacchetto in un computer che dispone già di SQL Server 2017 installato.

1. Installare **mssql-server agent** con il comando appropriato per il sistema operativo Linux.

   | Piattaforma | Comandi di installazione |
   |-----|-----|
   | RHEL | `sudo yum install mssql-server-agent` |
   | SLES | `sudo zypper refresh`<br/>`sudo zypper update mssql-server-agent` |
   | Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server-agent` |

1. Riavviare SQL Server con il comando seguente:

```
   sudo systemctl restart mssql-server
```

**Creare un database di esempio**


Utilizzare la procedura seguente per creare un database di esempio denominato **SampleDB**. Questo database viene utilizzato per il processo di backup giornaliero.

1. Nel computer Linux, aprire una sessione terminal bash.



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7. &nbsp;[Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md)

*Ultimo aggiornamento: 2017-12-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_6) | [Avanti](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880 eedddcfb64c6432215f56b74dc91700d9804fce8  (PR=4160  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=085dd05d56afecbb454206ed8402cfbaa597cfbe) -->



**<a id="repositories"></a>Configurare il repository di origine**


Quando si installa o si aggiorna SQL Server, ottenere la versione più recente di SQL Server dal repository Microsoft configurato.

**Opzioni di repository**


Esistono due tipi principali di repository per ogni distribuzione:

- **Gli aggiornamenti cumulativi (CU)**: l'aggiornamento cumulativo (CU) repository contiene i pacchetti per la versione di SQL Server base ed eventuali correzioni o miglioramenti Release. Gli aggiornamenti cumulativi sono specifici di una versione di rilascio, ad esempio SQL Server 2017. Essi vengono rilasciati a un ritmo regolare.

- **GDR**: GDR il repository contiene i pacchetti per la versione di SQL Server base solo gli aggiornamenti critici e aggiornamenti della sicurezza perché tale versione. Questi aggiornamenti vengono inoltre aggiunti alla versione di aggiornamento Cumulativo successiva.

Ogni versione CU e GDR contiene il pacchetto di SQL Server completo e tutti gli aggiornamenti precedenti per il repository. L'aggiornamento da una versione GDR a una versione aggiornamento Cumulativo è supportato modificando il repository configurato per SQL Server. È anche possibile [effettuare il downgrade - #rollback) per qualsiasi versione entro il numero di versione principale (ad esempio: 2017). L'aggiornamento da un pacchetto CU versione a una versione GDR non è supportata.

**Controllare il repository configurato**


Se si desidera verificare il repository sia configurato, è possibile utilizzare le seguenti tecniche dipendente dalla piattaforma.

| Piattaforma | Procedura |
|-----|-----|
| RHEL | 1. Visualizzare i file di **/etc/yum.repos.d** directory:`sudo ls /etc/yum.repos.d`<br/>2. Cercare un file che configura la directory di SQL Server, ad esempio **mssql server.repo**.<br/>3. Stampare il contenuto del file:`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4. Il **nome** proprietà è il repository configurato.|
| SLES | 1. Eseguire il comando seguente: `sudo zypper info mssql-server`<br/>2. Il **Repository** proprietà è il repository configurato. |
| Ubuntu | 1. Eseguire il comando seguente: `sudo cat /etc/apt/sources.list`<br/>2. Esaminare l'URL del pacchetto per mssql server. |



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-configure-failover-cluster-instance---sql-server-on-linux-rhelsql-server-linux-shared-disk-cluster-configuremd"></a>8. &nbsp;[Istanza cluster di failover Configura: SQL Server in Linux (RHEL)](sql-server-linux-shared-disk-cluster-configure.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_7) | [Avanti](#TitleNum_9))

<!-- Source markdown line 25.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 308fa1809c80a009f7f15b5ca6917f6b76588c3e 71f18baa320041ff10c94e8c7668e40dff45cac3  (PR=4150  ,  Filename=sql-server-linux-shared-disk-cluster-configure.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



> [!div class="checklist"]
> * Installare e configurare Linux
> * Installare e configurare SQL Server
> * Configurare il file hosts
> * Configurare l'archiviazione condivisa e spostare i file di database
> * Installare e configurare Pacemaker su ogni nodo del cluster
> * Configurare l'istanza del cluster di failover

In questo articolo viene illustrato come creare un'istanza di cluster di failover (FCI) disco condiviso a due nodi per SQL Server. L'articolo include istruzioni ed esempi di script per Red Hat Enterprise Linux (RHEL). Ubuntu distribuzioni sono simili a RHEL pertanto gli esempi di script in genere funzionano anche in Ubuntu.

Per ulteriori informazioni, vedere [SQL Server Cluster di Failover istanza (FCI) nel Linux--sql-server-linux-shared-disk-cluster-concepts.md).

**Prerequisiti**


Per completare lo scenario end-to-end seguente devono essere presenti due macchine per distribuire il cluster a due nodi e un altro server per l'archiviazione. Passaggi seguenti viene descritto come questi server verranno configurati.

**Installare e configurare Linux**


Il primo passaggio consiste nel configurare il sistema operativo nei nodi del cluster. In ogni nodo del cluster, configurare una distribuzione di linux. Utilizzare la stessa distribuzione e la versione in entrambi i nodi. Utilizzare uno o l'altra le seguenti distribuzioni:

* RHEL con una sottoscrizione valida per il componente aggiuntivo a disponibilità elevata

**Installare e configurare SQL Server**


1. Installare e configurare SQL Server in entrambi i nodi.  Per istruzioni dettagliate, vedere [installazione di SQL Server in Linux - sql-server-linux-setup.md.)
1. Specificare un nodo primario e l'altro come secondario, ai fini di configurazione. Utilizzare questi termini per le operazioni seguenti in questa Guida.
1. Nel nodo secondario, arrestare e disabilitare il Server SQL.
    Nell'esempio seguente arresta e disattiva SQL Server:
```
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
```

    > [!NOTE]
    > At set up time, a Server Master Key is generated for the SQL Server instance and placed at `var/opt/mssql/secrets/machine-key`. On Linux, SQL Server always runs as a local account called mssql. Because it's a local account, its identity isn't shared across nodes. Therefore, you need to copy the encryption key from primary node to each secondary node so each local mssql account can access it to decrypt the Server Master Key.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-troubleshoot-sql-server-on-linuxsql-server-linux-troubleshooting-guidemd"></a>9. &nbsp;[Risolvere i problemi relativi a SQL Server in Linux](sql-server-linux-troubleshooting-guide.md)

*Aggiornamento: 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f8557a34b38e028ff6e5ac370b6d2d6bf315091 196e56187b57bdd79cc5cdc5e6fce3d41e82af0c  (PR=4150  ,  Filename=sql-server-linux-troubleshooting-guide.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**Avvio di SQL Server nella configurazione minima o in modalità utente singolo**


**Avvio di SQL Server in modalità configurazione minima**

È utile nel caso in cui l'impostazione di un valore di configurazione, ad esempio un'allocazione eccessiva di memoria, abbia impedito l'avvio del server.

```
   sudo -u mssql /opt/mssql/bin/sqlservr -f
```

**Avvio di SQL Server in modalità utente singolo**

In determinate circostanze, è possibile avviare un'istanza di SQL Server in modalità utente singolo utilizzando l'opzione di avvio -m. Ad esempio, può risultare utile modificare le opzioni di configurazione del server oppure recuperare un database master o un altro database di sistema danneggiato. Ad esempio, è consigliabile modificare le opzioni di configurazione di server oppure recuperare un database master danneggiato o altri database di sistema

Avvio di SQL Server in modalità utente singolo
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m
```

Avvio di SQL Server in modalità utente singolo con SQLCMD
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
```

> [!WARNING]
>  Avviare SQL Server in Linux con l'utente "mssql" per evitare problemi di avvio futuri. Esempio "sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]"

Se si è iniziato a accidentalmente SQL Server con un altro utente, è necessario modificare il proprietario dei file di database di SQL Server all'utente prima dell'avvio di SQL Server con systemd 'mssql'. Ad esempio, eseguire il comando seguente per modificare la proprietà di tutti i file di database in /var/opt/mssql all'utente 'mssql',

```
   chown -R mssql:mssql /var/opt/mssql/
```







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse che hanno gli articoli di nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1 + 0): **Analysis Services per SQL** documenti](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0 + 1): **SQL Server Data Tools (SSDT)** documenti](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0 + 1): **SQL Server Management Studio (SSMS)** documenti](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse che non dispone di alcun nuovo o aggiornati di recente articoli

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0 + 0): **oggetti ADO (ActiveX Data) per SQL** documenti](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0 + 0): **ODBC (Open Database Connectivity) per SQL** documenti](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0 + 0): **PowerShell per SQL** documenti](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0 + 0): **XQuery per SQL** documenti](../xquery/new-updated-xquery.md)


