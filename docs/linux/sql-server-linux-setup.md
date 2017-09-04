---
title: Installazione di SQL Server 2017 in Linux | Documenti Microsoft
description: Installare, aggiornare e disinstallare SQL Server in Linux. Questo argomento descrive scenari online, offline e automatici.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.translationtype: MT
ms.sourcegitcommit: 303d3b74da3fe370d19b7602c0e11e67b63191e7
ms.openlocfilehash: f746037f695301881ce9a993f3d556db44f44292
ms.contentlocale: it-it
ms.lasthandoff: 08/29/2017

---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Guida all'installazione per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo argomento viene illustrato come installare, aggiornare e disinstallare 2017 di SQL Server in Linux. SQL Server 2017 RC2 è supportato in Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) e Ubuntu. È inoltre disponibile come un'immagine di Docker, che può essere eseguita nel motore Docker in Linux o Docker per Windows/Mac.

> [!TIP]
> Per iniziare rapidamente, passare a una delle esercitazioni di avvio rapido per [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), o [Docker](quickstart-install-connect-docker.md).

## <a id="supportedplatforms"></a>Piattaforme supportate

2017 di SQL Server è supportato sulle piattaforme Linux seguenti:

| Piattaforma | Versioni supportate | Recupero
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 | [Ottenere RHEL 7.3](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | SP2 (V12) | [Ottenere SLES v12 SP2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Ottenere Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Motore docker** | 1.8+ | [Ottenere Docker](http://www.docker.com/products/overview)

## <a id="system"></a>Requisiti di sistema

SQL Server 2017 presenta i requisiti di sistema seguenti per Linux:

|||
|-----|-----|
| **Memoria** | 3.25 GB |
| **File system** | **XFS** o **EXT4** (altri file System, ad esempio **BTRFS**, non sono supportati) |
| **Spazio su disco** | 6 GB |
| **Velocità del processore** | 2 GHz |
| **Core del processore** | 2 core |
| **Tipo di processore** | solo x64 compatibile |

> [!NOTE]
> Motore di SQL Server è stato testato fino a 1 TB di memoria in questo momento.

## <a id="platforms"></a> Installare SQL Server

È possibile installare SQL Server in Linux dalla riga di comando. Per istruzioni, vedere una delle esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)

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

> [!IMPORTANT]
> Downgrade è supportato solo tra RC2 e RC1 in questo momento.

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

