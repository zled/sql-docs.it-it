---
title: Guida all'installazione per SQL Server 2017 in Linux | Documenti Microsoft
description: Installare, aggiornare e disinstallare SQL Server in Linux. In questo articolo vengono illustrati scenari online, offline e automatici.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/06/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.workload: Active
ms.openlocfilehash: 98f7f19bbcf7ba83d74c2d4aa1e54409c2434147
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Guida all'installazione per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo vengono fornite indicazioni per l'installazione, aggiornamento e disinstallazione di SQL Server 2017 in Linux.

> [!TIP]
> Questa Guida coves diversi scenari di distribuzione. Se si sta cercando solo istruzioni dettagliate sull'installazione, passare a una delle Guide rapide:
> - [Guida introduttiva RHEL](quickstart-install-connect-red-hat.md)
> - [Guida introduttiva SLES](quickstart-install-connect-suse.md)
> - [Guida introduttiva di Ubuntu](quickstart-install-connect-ubuntu.md)
> - [Guida introduttiva di docker](quickstart-install-connect-docker.md)

Per le risposte alle domande più frequenti, vedere il [SQL Server in domande frequenti su Linux](../linux/sql-server-linux-faq.md).

## <a id="supportedplatforms"></a> Piattaforme supportate

2017 di SQL Server è supportato in Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) e Ubuntu. È anche supportato come immagine di Docker, che può essere eseguita nel motore Docker in Linux o Docker per Windows/Mac.

| Piattaforma | Versioni supportate | Recupero
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 o 7.4 | [Ottenere RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [Ottenere SLES v12 SP2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Get Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Motore docker** | 1.8+ | [Ottenere Docker](http://www.docker.com/products/overview)

Microsoft supporta anche la distribuzione e gestione dei contenitori di SQL Server utilizzando OpenShift e Kubernetes.

> [!NOTE]
> SQL Server viene testato e supportato in Linux per le distribuzioni elencate in precedenza. Se si sceglie di installare SQL Server in un sistema operativo non supportato, consultare il **criteri di supporto** sezione del [criteri di supporto tecnico per Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) per comprendere il supporto implicazioni.

## <a id="system"></a> Requisiti di sistema

SQL Server 2017 presenta i requisiti di sistema seguenti per Linux:

|||
|-----|-----|
| **Memoria** | 2 GB |
| **File system** | **XFS** o **EXT4** (altri file System, ad esempio **BTRFS**, non sono supportati) |
| **Spazio su disco** | 6 GB |
| **Velocità del processore** | 2 GHz |
| **Core del processore** | 2 core |
| **Tipo di processore** | solo x64 compatibile |

Se si utilizza **File System NFS (Network)** condivisioni remote nell'ambiente di produzione, tenere presente i requisiti di supporto seguenti:

- Utilizzare la versione NFS **4.2 o versioni successive**. Le versioni precedenti di NFS non supportano le funzionalità necessarie, ad esempio fallocate e creazione di file sparse, comune a sistemi di file più recenti.
- Individuare solo i **/var/opt/mssql** directory di montaggio NFS. Altri file, ad esempio i file binari del sistema di SQL Server, non sono supportati.
- Assicurarsi che i client NFS utilizzino l'opzione 'nolock' durante il montaggio condivisione remota.

## <a id="repositories"></a> Configurare il repository di origine

Quando si installa o si aggiorna SQL Server, è ottenere la versione più recente di SQL Server 2017 dal repository Microsoft configurato. Utilizzano le guide rapide di **aggiornamento cumulativo (CU)** repository. Ma è invece possibile configurare il **GDR** repository. Per ulteriori informazioni sul repository e sulla loro configurazione, vedere [configurare repository per SQL Server in Linux](sql-server-linux-change-repo.md).

> [!IMPORTANT]
> Se si è precedentemente installato una versione CTP o versione RC di SQL Server 2017, è necessario rimuovere il repository di anteprima e registrare un GA (General Availability) uno. Per ulteriori informazioni, vedere [configurare repository per SQL Server in Linux](sql-server-linux-change-repo.md).

## <a id="platforms"></a> Installare SQL Server

È possibile installare SQL Server in Linux dalla riga di comando. Per istruzioni, vedere una delle Guide rapide seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="upgrade"></a> Aggiornare SQL Server

Per aggiornare il **mssql server** alla versione più recente del pacchetto, utilizzare uno dei seguenti comandi basati sulla piattaforma:

| Piattaforma | Comandi di aggiornamento pacchetto |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Questi comandi scaricano il pacchetto più recente e sostituire i file binari sotto `/opt/mssql/`. L'utente ha generato i database e i database di sistema non sono interessati da questa operazione.

## <a id="rollback"></a> Ripristino SQL Server

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

## <a id="versioncheck"></a> Controllo versione installata di SQL Server

Per verificare la versione corrente e l'edizione di SQL Server in Linux, usare la procedura seguente:

1. Se non è già installato, installare il [gli strumenti da riga di comando di SQL Server](sql-server-linux-setup-tools.md).

1. Utilizzare **sqlcmd** per eseguire il comando Transact-SQL che consente di visualizzare la versione di SQL Server e l'edizione.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a> Disinstallare SQL Server

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

## <a id="unattended"></a> Installazione automatica

È possibile eseguire un'installazione automatica nel modo seguente:

- Attenersi alla procedura iniziale nel [Guide rapide](#platforms) per registrare il repository e installare SQL Server.
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

## <a id="offline"></a> Installazione offline

Se il computer Linux non ha accesso per i repository online usati nel [introduttive](#platforms), è possibile scaricare direttamente i file del pacchetto. Questi pacchetti si trovano nel repository Microsoft [ https://packages.microsoft.com ](https://packages.microsoft.com).

> [!TIP]
> Se è installato correttamente con i passaggi descritti in avvio rapido, non è necessario scaricare o installare manualmente i pacchetti di SQL Server. In questa sezione è solo per lo scenario offline.

1. **Scaricare il pacchetto del motore di database per la piattaforma**. Trovare i collegamenti ai download del pacchetto nella sezione dei dettagli del pacchetto del [note sulla versione](sql-server-linux-release-notes.md).

1. **Spostare il pacchetto scaricato nel computer Linux**. Se si usa un altro computer per scaricare i pacchetti, è possibile spostare i pacchetti nel computer Linux è con il **scp** comando.

1. **Installare il pacchetto di motore di database**. Utilizzare uno dei seguenti comandi basati sulla piattaforma. Sostituire il nome file del pacchetto in questo esempio con il nome esatto di che cui è stato scaricato.

   | Piattaforma | Comando di installazione del pacchetto |
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

## <a name="optional-sql-server-features"></a>Funzionalità facoltative di SQL Server

Dopo l'installazione, è anche possibile installare o abilitare le funzionalità facoltative di SQL Server.

- [Strumenti da riga di comando di SQL Server](sql-server-linux-setup-tools.md)
- [SQL Server Agent](sql-server-linux-setup-sql-agent.md)
- [Ricerca Full-Text SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

> [!TIP]
> Per le risposte alle domande più frequenti, vedere il [SQL Server in domande frequenti su Linux](sql-server-linux-faq.md).
