---
title: Installazione di SQL Server 2017 in Linux | Documenti Microsoft
description: Installare, aggiornare e disinstallare SQL Server in Linux. Questo argomento descrive scenari online, offline e automatici.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/26/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.workload: Active
ms.openlocfilehash: 65835ac1faf75664ecdbac8907c74906ccc4175e
ms.sourcegitcommit: 085dd05d56afecbb454206ed8402cfbaa597cfbe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Guida all'installazione per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo argomento viene illustrato come installare, aggiornare e disinstallare 2017 di SQL Server in Linux. 2017 di SQL Server è supportato in Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) e Ubuntu. È inoltre disponibile come un'immagine di Docker, che può essere eseguita nel motore Docker in Linux o Docker per Windows/Mac.

> [!TIP]
> Per iniziare rapidamente, passare a una delle esercitazioni di avvio rapido per [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), o [Docker](quickstart-install-connect-docker.md).

## <a id="supportedplatforms"></a>Piattaforme supportate

2017 di SQL Server è supportato sulle piattaforme Linux seguenti:

| Piattaforma | Versioni supportate | Recupero
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 o 7.4 | [Ottenere RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | SP2 (V12) | [Ottenere SLES v12 SP2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Ottenere Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Motore docker** | 1.8+ | [Ottenere Docker](http://www.docker.com/products/overview)

## <a id="system"></a>Requisiti di sistema

SQL Server 2017 presenta i requisiti di sistema seguenti per Linux:

|||
|-----|-----|
| **Memoria** | 2 GB |
| **File System** | **XFS** o **EXT4** (altri file System, ad esempio **BTRFS**, non sono supportati) |
| **Spazio su disco** | 6 GB |
| **Velocità del processore** | 2 GHz |
| **Core del processore** | 2 core |
| **Tipo di processore** | solo x64 compatibile |

Se si utilizza **File System NFS (Network)** condivisioni remote nell'ambiente di produzione, tenere presente i requisiti di supporto seguenti:

- Utilizzare la versione NFS **4.2 o versioni successive**. Le versioni precedenti di NFS non supportano le funzionalità necessarie, ad esempio fallocate e creazione di file sparse, comune a sistemi di file più recenti.
- Individuare solo i **/var/opt/mssql** directory di montaggio NFS. Altri file, ad esempio i file binari del sistema di SQL Server, non sono supportati.
- Assicurarsi che i client NFS utilizzino l'opzione 'nolock' durante il montaggio condivisione remota.

## <a id="platforms"></a> Installare SQL Server

È possibile installare SQL Server in Linux dalla riga di comando. Per istruzioni, vedere una delle esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="upgrade"></a>Aggiornare SQL Server

Per aggiornare il **mssql server** alla versione più recente del pacchetto, utilizzare uno dei seguenti comandi basati sulla piattaforma:

| Piattaforma | Comandi di aggiornamento pacchetto |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Questi comandi scaricano il pacchetto più recente e sostituire i file binari sotto `/opt/mssql/`. L'utente ha generato i database e i database di sistema non sono interessati da questa operazione.

## <a id="rollback"></a>Ripristino SQL Server

Per eseguire il rollback o il downgrade da SQL Server a una versione precedente, attenersi alla procedura seguente:

1. Identificare il numero di versione per il pacchetto di SQL Server che si desidera effettuare il downgrade a. Per un elenco di numeri di pacchetto, vedere il [note sulla versione](sql-server-linux-release-notes.md).

1. Effettuare il downgrade a una versione precedente di SQL Server. Nei comandi seguenti, sostituire `<version_number>` con il numero di versione di SQL Server è identificato nel passaggio 1.

   | Piattaforma | Comandi di aggiornamento pacchetto |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> È supportato solo per effettuare il downgrade a una versione all'interno della stessa versione principale, ad esempio SQL Server 2017.

## <a id="versioncheck"></a>Controllo versione installata di SQL Server

Per verificare la versione corrente e l'edizione di SQL Server in Linux, usare la procedura seguente:

1. Se non è già installato, installare il [gli strumenti da riga di comando di SQL Server](sql-server-linux-setup-tools.md).

1. Utilizzare **sqlcmd** per eseguire il comando Transact-SQL che consente di visualizzare la versione di SQL Server e l'edizione.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a>Disinstallare SQL Server

Per rimuovere il **mssql server** pacchetto in Linux, utilizzare uno dei seguenti comandi basati sulla piattaforma:

| Piattaforma | Comandi per la rimozione del pacchetto |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

La rimozione del pacchetto non elimina i file di database generato. Se si desidera eliminare i file di database, utilizzare il comando seguente:

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="repositories"></a>Configurare il repository di origine

Quando si installa o si aggiorna SQL Server, ottenere la versione più recente di SQL Server dal repository Microsoft configurato.

### <a name="repository-options"></a>Opzioni di repository

Esistono due tipi principali di repository per ogni distribuzione:

- **Gli aggiornamenti cumulativi (CU)**: l'aggiornamento cumulativo (CU) repository contiene i pacchetti per la versione di SQL Server base ed eventuali correzioni o miglioramenti Release. Gli aggiornamenti cumulativi sono specifici di una versione di rilascio, ad esempio SQL Server 2017. Essi vengono rilasciati a un ritmo regolare.

- **GDR**: GDR il repository contiene i pacchetti per la versione di SQL Server base solo gli aggiornamenti critici e aggiornamenti della sicurezza perché tale versione. Questi aggiornamenti vengono inoltre aggiunti alla versione di aggiornamento Cumulativo successiva.

Ogni versione CU e GDR contiene il pacchetto di SQL Server completo e tutti gli aggiornamenti precedenti per il repository. L'aggiornamento da una versione GDR a una versione aggiornamento Cumulativo è supportato modificando il repository configurato per SQL Server. È anche possibile [effettuare il downgrade](#rollback) per qualsiasi versione entro il numero di versione principale (ad esempio: 2017). L'aggiornamento da un pacchetto CU versione a una versione GDR non è supportata.

### <a name="check-your-configured-repository"></a>Controllare il repository configurato

Se si desidera verificare il repository sia configurato, è possibile utilizzare le seguenti tecniche dipendente dalla piattaforma.

| Piattaforma | Procedura |
|-----|-----|
| RHEL | 1. Visualizzare i file di **/etc/yum.repos.d** directory:`sudo ls /etc/yum.repos.d`<br/>2. Cercare un file che configura la directory di SQL Server, ad esempio **mssql server.repo**.<br/>3. Stampare il contenuto del file:`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4. Il **nome** proprietà è il repository configurato.|
| SLES | 1. Eseguire il comando seguente: `sudo zypper info mssql-server`<br/>2. Il **Repository** proprietà è il repository configurato. |
| Ubuntu | 1. Eseguire il comando seguente: `sudo cat /etc/apt/sources.list`<br/>2. Esaminare l'URL del pacchetto per mssql server. |

Fine dell'URL del repository conferma che il tipo di repository:

- **MSSQL server**: repository di anteprima.
- **MSSQL-server-2017**: CU repository.
- **MSSQL-server-2017-gdr**: repository GDR.

### <a name="change-the-source-repository"></a>Modificare il repository di origine

Per configurare il repository CU o GDR, attenersi alla procedura seguente:

> [!NOTE]
> Il [avvio rapido di esercitazioni](#platforms) configurare l'aggiornamento Cumulativo del repository. Se si seguono queste esercitazioni, non è necessario utilizzare la procedura seguente per continuare a usare il repository CU. Questi passaggi sono necessari solo per la modifica del repository configurato.

1. Se necessario, rimuovere il repository configurato in precedenza.

   | Piattaforma | Archivio | Comando di rimozione del repository |
   |---|---|---|
   | RHEL | **Tutto** | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | **CTP** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | | **AGGIORNAMENTO CUMULATIVO** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
   | | **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|
   | Ubuntu | **CTP** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
   | | **AGGIORNAMENTO CUMULATIVO** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
   | | **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

1. Per **Ubuntu solo**, importare le chiavi GPG archivio pubblico.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Configurare il nuovo repository.

   | Piattaforma | Archivio | Command |
   |-----|-----|-----|
   | RHEL | AGGIORNAMENTO CUMULATIVO | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | AGGIORNAMENTO CUMULATIVO  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | AGGIORNAMENTO CUMULATIVO | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [Installare](#platforms) o [aggiornare](#upgrade) SQL Server e i relativi pacchetti dal repository di nuovo.

   > [!IMPORTANT]
   > A questo punto, se si sceglie di utilizzare una delle esercitazioni di installazione, ad esempio il [esercitazioni delle Guide rapide](#platforms), tenere presente che si è appena configurato del repository di destinazione. Non ripetere il passaggio nelle esercitazioni. Ciò vale soprattutto se si configura il repository GDR, poiché le esercitazioni utilizzano il repository CU.

## <a id="unattended"></a>Installazione automatica

È possibile eseguire un'installazione automatica nel modo seguente:

- Attenersi alla procedura iniziale nel [esercitazioni di avvio rapido](#platforms) per registrare il repository e installare SQL Server.
- Quando si esegue `mssql-conf setup`, impostare [le variabili di ambiente](sql-server-linux-configure-environment-variables.md) e utilizzare il `-n` (Nessun prompt) opzione.

Nell'esempio seguente consente di configurare l'edizione Developer di SQL Server con il **MSSQL_PID** variabile di ambiente. Tale metodo accetta inoltre il contratto di licenza (**ACCEPT_EULA**) e imposta la password dell'utente amministratore (**MSSQL_SA_PASSWORD**). Il `-n` parametro consente di eseguire un'installazione unprompted in cui i valori di configurazione vengono estratti dalle variabili di ambiente.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

È anche possibile creare uno script che vengono eseguite altre azioni. Ad esempio, è possibile installare altri pacchetti di SQL Server.

Per un esempio più dettagliato, vedere gli esempi seguenti:

- [Red Hat script di installazione automatica](sample-unattended-install-redhat.md)
- [SUSE script di installazione automatica](sample-unattended-install-suse.md)
- [Ubuntu script di installazione automatica](sample-unattended-install-ubuntu.md)

## <a id="offline"></a>Installazione offline

Se il computer Linux non ha accesso per i repository online usati nel [introduttive](#platforms), è possibile scaricare direttamente i file del pacchetto. Questi pacchetti si trovano nel repository di Microsoft, [https://packages.microsoft.com](https://packages.microsoft.com).

> [!TIP]
> Se è installato correttamente con i passaggi descritti in avvio rapido, non è necessario scaricare o installare manualmente i pacchetti seguenti. In questa sezione è solo per lo scenario offline.

1. **Scaricare il pacchetto del motore di database per la piattaforma**. Trovare i collegamenti ai download del pacchetto nella sezione dei dettagli del pacchetto del [note sulla versione](sql-server-linux-release-notes.md).

1. **Spostare il pacchetto scaricato nel computer Linux**. Se si usa un altro computer per scaricare i pacchetti, è possibile spostare i pacchetti nel computer Linux è con il **scp** comando.

1. **Installare il pacchetto di motore di database**. Utilizzare uno dei seguenti comandi basati sulla piattaforma. Sostituire il nome file del pacchetto in questo esempio con il nome esatto di che cui è stato scaricato.

   | Piattaforma | Comando di rimozione del pacchetto |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > È inoltre possibile installare i pacchetti RPM (RHEL e SLES) con il `rpm -ivh` comando, ma i comandi nella tabella precedente se installano automaticamente le dipendenze disponibile dal repository di approvazione.

1. **Risolvere le dipendenze mancante**: è possibile avere dipendenze mancanti a questo punto. In caso contrario, è possibile ignorare questo passaggio. In Ubuntu, se si ha accesso al repository approvati contenente tali dipendenze, la soluzione più semplice consiste nell'utilizzare il `apt-get -f install` comando. Questo comando consente inoltre di completare l'installazione di SQL Server. Per controllare manualmente le dipendenze, usare i comandi seguenti:

   | Piattaforma | Comando di elenco delle dipendenze |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   Dopo aver risolto le dipendenze mancanti, tentare di installare nuovamente il pacchetto mssql server.

1. **Completare l'installazione di SQL Server**. Utilizzare **mssql conf** per completare l'installazione di SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>Passaggi successivi

Dopo l'installazione, è inoltre possibile installare altri pacchetti di SQL Server facoltativi.

- [Strumenti da riga di comando di SQL Server](sql-server-linux-setup-tools.md)
- [SQL Server Agent](sql-server-linux-setup-sql-agent.md)
- [Ricerca Full-Text SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

Connettersi all'istanza di SQL Server per avviare la creazione e la gestione dei database. Per iniziare, vedere le esercitazioni di avvio rapido:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
