---
title: Installare gli strumenti da riga di comando di SQL Server in Linux | Documenti Microsoft
description: In questo argomento viene descritto come installare gli strumenti di SQL Server in Linux.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 130da2409070f0acfda0bf78fcf2c4326bbeec92
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Installare sqlcmd e bcp strumenti da riga di comando di SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

I passaggi seguenti installare gli strumenti da riga di comando, i driver ODBC di Microsoft e le relative dipendenze. Il **mssql strumenti** pacchetto contiene:

- **SQLCMD**: utilità della riga di comando di query.
- **bcp**: utilità di esportazione di importazione Bulk.

Installare gli strumenti per la piattaforma:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

In questo argomento viene descritto come installare gli strumenti da riga di comando. Se si sta cercando esempi dell'utilizzo di **sqlcmd** o **bcp**, vedere il [collegamenti](#next-steps) alla fine di questo argomento.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Installare gli strumenti in RHEL 7

Utilizzare la procedura seguente per installare il **mssql strumenti** su Red Hat Enterprise Linux. 

1. Passare alla modalità utente avanzato.

   ```bash
   sudo su
   ```

1. Scaricare il file di configurazione di repository Microsoft Red Hat.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Uscire dalla modalità utente avanzato.

   ```bash
   exit
   ```

1. Se si dispone di una versione precedente di **mssql strumenti** installato, rimuovere tutti i pacchetti meno recenti di unixODBC.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Eseguire i comandi seguenti per installare **mssql strumenti** con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Per l'aggiornamento alla versione più recente di **mssql strumenti** eseguire i comandi seguenti:
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Parametro facoltativo**: aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente in una shell bash.

   Per rendere **sqlcmd/bcp** accessibile da shell bash per le sessioni di accesso, modificare il **percorso** nel **~/.bash_profile** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Per rendere **sqlcmd/bcp** accessibile da shell bash per le sessioni/non-accesso interattivo, modificare il **percorso** nel **~/.bashrc** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Installare gli strumenti in 16.04 Ubuntu

Utilizzare la procedura seguente per installare il **mssql strumenti** in Ubuntu. 

1. Importare le chiavi GPG archivio pubblico.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrare il repository Ubuntu Microsoft.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Aggiornare l'elenco delle origini ed eseguire il comando di installazione con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Per l'aggiornamento alla versione più recente di **mssql strumenti** eseguire i comandi seguenti:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Parametro facoltativo**: aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente in una shell bash.

   Per rendere **sqlcmd/bcp** accessibile da shell bash per le sessioni di accesso, modificare il **percorso** nel **~/.bash_profile** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Per rendere **sqlcmd/bcp** accessibile da shell bash per le sessioni/non-accesso interattivo, modificare il **percorso** nel **~/.bashrc** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Installare gli strumenti in SLES 12

Utilizzare la procedura seguente per installare il **mssql strumenti** in SUSE Linux Enterprise Server. 

1. Aggiungere Zypper il repository di Microsoft SQL Server.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installare **mssql strumenti** con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Per l'aggiornamento alla versione più recente di **mssql strumenti** eseguire i comandi seguenti:
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Parametro facoltativo**: aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente in una shell bash.

   Per rendere **sqlcmd/bcp** accessibile da shell bash per le sessioni di accesso, modificare il **percorso** nel **~/.bash_profile** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Per rendere **sqlcmd/bcp** accessibile da shell bash per le sessioni/non-accesso interattivo, modificare il **percorso** nel **~/.bashrc** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a>Installare gli strumenti in macOS

Anteprima di **sqlcmd** e **bcp** è ora disponibile in macOS. Per ulteriori informazioni, vedere il [annuncio](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

Per installare gli strumenti per montagna di El Capitan Mac e Sierra, utilizzare i comandi seguenti:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
#brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox mssql-tools
#for silent install: 
#ACCEPT_EULA=y brew install --no-sandbox mssql-tools
```

## <a id="docker"></a>Docker

A partire da SQL Server 2017 CTP 2.0, gli strumenti da riga di comando di SQL Server sono inclusi nell'immagine di Docker. Se si collega all'immagine con un prompt dei comandi interattivi, è possibile eseguire gli strumenti in locale.

## <a name="offline-installation"></a>Installazione offline

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

Nella tabella seguente fornisce il percorso per i pacchetti di strumenti più recenti:

| Pacchetto di strumenti | Version | Scarica |
|-----|-----|-----|
| Pacchetto di strumenti di Red Hat RPM | 14.0.5.0-1 | [pacchetto RPM MSSQL strumenti](https://packages.microsoft.com/rhel/7.3/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Pacchetto di strumenti SLES RPM | 14.0.5.0-1 | [pacchetto RPM MSSQL strumenti](https://packages.microsoft.com/sles/12/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian pacchetto degli strumenti | 14.0.5.0-1 | [pacchetto Debian MSSQL strumenti](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |
| Ubuntu 16.10 Debian pacchetto degli strumenti | 14.0.5.0-1 | [pacchetto Debian MSSQL strumenti](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |

Questi pacchetti dipendono da **ha**, che deve essere installato per primo. Il **ha** quest'ultimo ha anche una dipendenza su **esposti all'interno di unixODBC** (RPM) o **unixodbc-dev** (Debian). Il percorso del **ha** nella tabella seguente vengono elencati i pacchetti:

| pacchetto ha | Version | Scarica |
|-----|-----|-----|
| Pacchetto ha Red Hat RPM | 13.1.6.0-1 | [pacchetto RPM ha](https://packages.microsoft.com/rhel/7.3/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Pacchetto ha SLES RPM | 13.1.6.0-1 | [pacchetto RPM ha](https://packages.microsoft.com/sles/12/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Ubuntu 16.04 ha Debian pacchetto | 13.1.6.0-1 | [pacchetto Debian ha](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |
| Pacchetto Debian ha Ubuntu 16.10 | 13.1.6.0-1 | [pacchetto Debian ha](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |

Per installare manualmente questi pacchetti, attenersi alla procedura seguente:

1. **Spostare i pacchetti scaricati nel computer Linux**. Se si usa un altro computer per scaricare i pacchetti, è possibile spostare i pacchetti nel computer Linux è con il **scp** comando.

1. **Installare i pacchetti e**: installare il **mssql strumenti** e **msodbc** pacchetti. Se si verificano errori di dipendenza, è possibile ignorarli fino al passaggio successivo.

    | Piattaforma | Comandi di installazione del pacchetto |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo yum localinstall mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | SLES | `sudo zypper install msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo zypper install mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_13.1.6.0-1_amd64.deb`<br/>`sudo dpkg -i mssql-tools_14.0.5.0-1_amd64.deb` |

1. **Risolvere le dipendenze mancante**: è possibile avere dipendenze mancanti a questo punto. In caso contrario, è possibile ignorare questo passaggio. In alcuni casi, è necessario individuare manualmente e installare le dipendenze.

    Per i pacchetti RPM, è possibile controllare le dipendenze necessarie con i comandi seguenti:

    ```bash
    rpm -qpR msodbcsql-13.1.6.0-1.x86_64.rpm
    rpm -qpR mssql-tools-14.0.5.0-1.x86_64.rpm
    ```

    Per pacchetti Debian, se si ha accesso al repository approvati contenente tali dipendenze, la soluzione più semplice consiste nell'utilizzare il **apt get** comando:

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Questo comando completa l'installazione di nonché i pacchetti di SQL Server.

    Se non funziona per il pacchetto Debian, è possibile esaminare le dipendenze necessarie con i comandi seguenti:

    ```bash
    dpkg -I msodbcsql_13.1.6.0-1_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_14.0.5.0-1_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Passaggi successivi

Per un esempio di come utilizzare **sqlcmd** per connettersi a SQL Server e creare un database, vedere uno dei seguente rapido avviare esercitazioni:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)

Per un esempio di come utilizzare **bcp** per importazione ed esportazione bulk dei dati, vedere [copia Bulk di dati a SQL Server in Linux](sql-server-linux-migrate-bcp.md).

