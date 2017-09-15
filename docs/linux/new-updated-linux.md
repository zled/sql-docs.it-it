---
title: 'Aggiornato: SQL Server in Linux docs | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per Microsoft SQL Server in Linux.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 9e6b139e45ccb5184255eabedfb0f809ff64fd2b
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nuovi e recentemente aggiornato: SQL Server in Linux documenti



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-07-18** &nbsp; - a - &nbsp; **2017-09-11**
- *Area di interesse:* &nbsp; **Microsoft SQL Server in Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti portano a nuovi articoli che sono stati aggiunti di recente.


1. [Posta elettronica database e gli avvisi di posta elettronica con SQL Agent in Linux](sql-server-linux-db-mail-sql-agent.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati che sono elencati nella sezione estratti.

1. [Funzioni gruppo di disponibilità elevata per SQL Server in Linux](#TitleNum_1)
2. [Configurare le immagini contenitore di SQL Server 2017 in Docker](#TitleNum_2)
3. [Configurare SQL Server in Linux con lo strumento mssql conf](#TitleNum_3)
4. [Suggerimenti dei clienti per SQL Server in Linux](#TitleNum_4)
5. [Eseguire la migrazione di un database di SQL Server da Windows per Linux tramite backup e ripristino](#TitleNum_5)
6. [Note sulla versione di SQL Server 2017 su Linux](#TitleNum_6)
7. [Guida all'installazione per SQL Server in Linux](#TitleNum_7)
8. [Installare SQL Server Integration Services (SSIS) in Linux](#TitleNum_8)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-operate-ha-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-failover-hamd"></a>1. &nbsp;[Operano a disponibilità elevata gruppo di disponibilità per SQL Server in Linux](sql-server-linux-availability-group-failover-ha.md)

*Ultimo aggiornamento: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 167.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1bef3ece125721b041aa2b9d836329736377df8d 669d2b9a614d680b98280d5b522ba82cf466536c  (PR=2948  ,  Filename=sql-server-linux-availability-group-failover-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



**Aggiornare il gruppo di disponibilità**


Prima di aggiornare un gruppo di disponibilità, esaminare le procedure consigliate in [aggiornamento disponibilità gruppo replica istanze-... / database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Le sezioni seguenti illustrano come eseguire un aggiornamento in sequenza con istanze di SQL Server in Linux con gruppi di disponibilità.

**Passaggi di aggiornamento su Linux**


Quando repliche del gruppo di disponibilità si trovano in istanze di SQL Server in Linux, il tipo di cluster del gruppo di disponibilità è `EXTERNAL` o `NONE`. Un gruppo di disponibilità che è gestito da Gestione cluster di diversi da Windows Server Failover Cluster (WSFC) `EXTERNAL`. Pacemaker con Corosync è riportato un esempio di Gestione cluster esterno. Dispone di un gruppo di disponibilità con alcuna Gestione cluster di tipo cluster `NONE` i passaggi di aggiornamento descritti di seguito sono specifici per i gruppi di disponibilità di tipo cluster `EXTERNAL` o `NONE`.

1. Prima di iniziare, eseguire il backup ogni database.
2. Aggiornare le istanze di SQL Server di ospitare le repliche secondarie.

    a. Prima di tutto aggiornare repliche secondarie asincrone.

    b. Aggiornare le repliche secondarie sincrone.

   >[!NOTE]
   >Se un gruppo di disponibilità dispone solo di asincrona repliche - per evitare eventuali perdite di dati modificare una replica sincrona e attendere fino a quando viene sincronizzata. Quindi aggiornare la replica.

   b. 1. Interrompere la risorsa nel nodo che ospita la replica secondaria di destinazione per l'aggiornamento

   Prima di eseguire il comando di aggiornamento, è possibile interrompere la risorsa in modo che il cluster non verrà monitorarlo e negativo inutilmente. Nell'esempio seguente aggiunge un vincolo di percorso sul nodo che si tradurrà sulla risorsa da arrestare. Aggiornamento `ag_cluster-master` con il nome della risorsa e `nodeName1` con il nodo che ospita la replica di destinazione per l'aggiornamento.

```
   pcs constraint location ag_cluster-master avoids nodeName1
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>2. &nbsp;[Configurare SQL Server 2017 le immagini contenitore Docker](sql-server-linux-configure-docker.md)

*Ultimo aggiornamento: 2017-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 257.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0239ed55a23721eedcc0407a0886d08da47c975b 108fe230151cff7dc91fcdc22218f232394746ec  (PR=3050  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=60272ce672c0a32738b0084ea86f8907ec7fc0a5) -->



1. Identificare il Docker **tag** per la versione che si desidera utilizzare. Per visualizzare i tag disponibili, vedere [pagina dell'hub Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Estrarre l'immagine del contenitore di SQL Server con il tag. Ad esempio, per eseguire il pull dell'immagine RC1, sostituire `<image_tag>` nel comando seguente con `rc1`.

```
   docker pull microsoft/mssql-server-linux:<image_tag>
```

1. Per eseguire un nuovo contenitore con l'immagine, specificare il nome di tag nel `docker run` comando. Il comando seguente, sostituire `<image_tag>` con la versione che si desidera eseguire.

```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

Questa procedura consente inoltre effettuare il downgrade di un contenitore esistente. Ad esempio, è possibile ripristinare o effettuare il downgrade di un contenitore per la risoluzione dei problemi o test in esecuzione. Per effettuare il downgrade di un contenitore in esecuzione, è necessario utilizzare una tecnica di persistenza per la cartella di dati. La stessa procedura descritta nel [aggiornare sezione-#upgrade), ma specificare il nome del tag della versione precedente, quando si esegue il nuovo contenitore.

> [!IMPORTANT]



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>3. &nbsp;[Configurare SQL Server in Linux con lo strumento mssql conf](sql-server-linux-configure-mssql-conf.md)

*Ultimo aggiornamento: 2017-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= lbosq.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6117f03e9617b70077488d86f94b32537c4cb9e8 4247a749c056037dd71a27121525be04be6a4f21  (PR=3042  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=46b16dcf147dbd863eec0330e87511b4ced6c4ce) -->



**<a id="localaudit"></a>Directory del set di controllo locale**


Il **telemetry.userrequestedlocalauditdirectory** impostazione Abilita controllo locale e consente di impostare la directory in cui i locale registri di controllo vengono creati.

1. Creare una directory di destinazione per i nuovi log di controllo locale. L'esempio seguente crea un nuovo **/tmp/controllo** directory:

```
   sudo mkdir /tmp/audit
```

1. Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

```
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
```

1. Eseguire lo script mssql conf come radice con il **impostare** comando **telemetry.userrequestedlocalauditdirectory**:

```
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
```

1. Riavviare il servizio SQL Server:

```
   sudo systemctl restart mssql-server
```

Per ulteriori informazioni, vedere [dei clienti per SQL Server in Linux--sql-server-linux-customer-feedback.md).

**<a id="lcid"></a>Modificare le impostazioni locali di SQL Server**


Il **language.lcid** modifiche alle impostazioni locali di SQL Server a qualsiasi identificatore di lingua supportata (LCID).

1. Nell'esempio seguente modifica le impostazioni locali sulla lingua francese (1036):

```
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
```

1. Riavviare il servizio SQL Server per applicare le modifiche:

```
   sudo systemctl restart mssql-server
```

**<a id="memorylimit"></a>Impostare il limite di memoria**


Il **memory.memorylimitmb** impostazione quantità memoria fisica (in MB) disponibile per SQL Server. Il valore predefinito è 80% della memoria fisica.

1. Eseguire lo script mssql conf come radice con il **impostare** comando **memory.memorylimitmb**. L'esempio seguente modifica la memoria disponibile per SQL Server a 3,25 GB (3328 MB).

```
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
```

1. Riavviare il servizio SQL Server per applicare le modifiche:



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-customer-feedback-for-sql-server-on-linuxsql-server-linux-customer-feedbackmd"></a>4. &nbsp;[i suggerimenti dei clienti per SQL Server in Linux](sql-server-linux-customer-feedback.md)

*Ultimo aggiornamento: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3) | [Avanti](#TitleNum_5))

<!-- Source markdown line 104.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9d8122e864804004d91f6b7c5c3d24c4a4114d34 7316ef831c390a854c324f23a02c3fb6005e2fea  (PR=2948  ,  Filename=sql-server-linux-customer-feedback.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->




**In Docker**

Per abilitare il controllo locale in docker è necessario disporre di Docker [vengono mantenute le data--sql-server-linux-configure-docker.md).

1. La directory di destinazione per i nuovi log di controllo locale sarà nel contenitore. Creare una directory di destinazione per i nuovi log di controllo locale nella directory nel computer host. L'esempio seguente crea un nuovo **/controllo** directory:

```
   sudo mkdir <host directory>/audit
```


1. Aggiungere un `mssql.conf` file con le righe `[telemetry]` e `userrequestedlocalauditdirectory = <host directory>/audit` nella directory host:

```
   echo '[telemetry]' >> <host directory>/mssql.conf
```

```
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
```
2. Esecuzione dell'immagine contenitore
```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

**Passaggi successivi**





&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restoresql-server-linux-migrate-restore-databasemd"></a>5. &nbsp;[Eseguire la migrazione di un database di SQL Server da Windows per Linux tramite backup e ripristino](sql-server-linux-migrate-restore-database.md)

*Ultimo aggiornamento: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_4) | [Avanti](#TitleNum_6))

<!-- Source markdown line 30.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e78f5516a46eab834f644979d3e1c0ca415fabcd 6b03a01385078290b9f451ac013b628f53e0e8b4  (PR=2948  ,  Filename=sql-server-linux-migrate-restore-database.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



* Computer Windows con le operazioni seguenti:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) installato.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) installato.
  * Database di destinazione per eseguire la migrazione.

* Computer Linux con installati i componenti seguenti:
  * SQL Server 2017 RC2. Vedere la Guida introduttiva di installazione per [RHEL--quickstart-install-connect-red-hat.md), [SLES - avvio rapido-installazione-connessione-suse.md) o [Ubuntu - avvio rapido-installazione-connessione-ubuntu.md).
  * SQL Server 2017 RC2 [tools--sql-server-linux-setup-tools.md della riga di comando).

**Creare un backup in Windows**


Esistono diversi modi per creare un file di backup di un database in Windows. La procedura seguente utilizza SQL Server Management Studio (SSMS).

1. Avviare **SQL Server Management Studio** sul proprio computer Windows.

1. Nella finestra di dialogo connessione immettere **localhost**.

1. In Esplora oggetti espandere **database**.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>6. &nbsp;[Note sulla versione di SQL Server 2017 su Linux](sql-server-linux-release-notes.md)

*Ultimo aggiornamento: 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_5) | [Avanti](#TitleNum_7))

<!-- Source markdown line 31.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4c8b9876f4792782314ba2f9b246405fb8036f84 acb97cf0a2e0bdd039575eaab9c41003316cbb02  (PR=2939  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



**<a id="RC2"></a>RC2 (agosto 2017)**


La versione del motore di SQL Server per questa versione è 14.0.900.75.

**Piattaforme supportate**


| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Installazione guide--quickstart-install-connect-red-hat.md) |
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione - avvio rapido-installazione-connessione-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guida all'installazione - avvio rapido-installazione-connessione-ubuntu.md) |
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione - avvio rapido-installazione-connessione-docker.md) |

> [!NOTE]
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1,5 TB di memoria in questo momento.

**Dettagli del pacchetto**


Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare i pacchetti direttamente se si utilizza la procedura nelle guide di installazione seguenti:

- [Installare il pacchetto di SQL Server - sql-server-linux-setup.md)
- [Installare package--sql-server-linux-setup-full-text-search.md di ricerca Full-text)
- [Installare SQL Server Agent package--sql-server-linux-setup-sql-agent.md)

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.900.75-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) |



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7. &nbsp;[Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md)

*Ultimo aggiornamento: 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_6) | [Avanti](#TitleNum_8))

<!-- Source markdown line 70.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00394e1733568a55243788d828968ff9b58a3c99 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880  (PR=2971  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=303d3b74da3fe370d19b7602c0e11e67b63191e7) -->



**<a id="rollback"></a>Ripristino SQL Server**


Per eseguire il rollback o il downgrade da SQL Server a una versione precedente, attenersi alla procedura seguente:

1. Identificare il numero di versione per il pacchetto di SQL Server che si desidera effettuare il downgrade a. Per un elenco di numeri di pacchetto, vedere [versione notes--sql-server-linux-release-notes.md).

1. Effettuare il downgrade a una versione precedente di SQL Server. Nei comandi seguenti, sostituire `<version_number>` con il numero di versione di SQL Server è identificato nel passaggio 1.

   | Piattaforma | Comandi di aggiornamento pacchetto |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> È supportato solo per effettuare il downgrade a una versione all'interno della stessa versione principale, ad esempio SQL Server 2017.

> [!IMPORTANT]
> Downgrade è supportato solo tra RC2 e RC1 in questo momento.




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-install-sql-server-integration-services-ssis-on-linuxsql-server-linux-setup-ssismd"></a>8. &nbsp;[Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)

*Ultimo aggiornamento: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_7))

<!-- Source markdown line 66.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a3fecd2553d1b25406445b8a26b22c9015dd98fe f836d560513fef1217e7dbce0ab85f78eec6f937  (PR=2948  ,  Filename=sql-server-linux-setup-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



Se si dispone già di `mssql-server-is` installato, è possibile aggiornare la versione più recente con il comando seguente:

```
sudo apt-get install mssql-server-is
```


Per rimuovere `mssql-server-is`, è possibile eseguire il seguente comando:
```
sudo apt-get remove msssql-server-is
```



**<a name="RHEL"></a>Installare SSIS in RHEL**

Per installare il `mssql-server-is` pacchetto su RHEL, seguire questi passaggi:


1.  Passare alla modalità utente avanzato.

```
    sudo su
```


2.  Scaricare il file di configurazione di Microsoft SQL Server Red Hat repository.

```
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
```


3.  Uscire dalla modalità utente avanzato.

```
    exit
```


4.  Eseguire i comandi seguenti per installare SQL Server Integration Services.

```
    sudo yum install -y mssql-server-is
```


5.  Dopo l'installazione, eseguire `ssis-conf`.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Questa sezione sono elencati gli articoli molto simili per gli articoli aggiornati di recente in altre aree di interesse, entro l'archivio pubblico di GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3 + 12): **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5 + 0): **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5 + 1): **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19 + 82): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1 + 8): **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12 + 1): **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0 + 1): **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7 + 1): **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1 + 1): **SQL Server Data Tools (SSDT)** documenti](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0 + 2): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1 + 4): **SQL Server Management Studio (SSMS)** documenti](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornati (4 + 1): **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0 + 1): **Tools per SQL** documenti](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0 + 0): **Analysis Services per SQL** documenti](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0 + 0): **Master Data Services (MDS) per SQL** documenti](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



