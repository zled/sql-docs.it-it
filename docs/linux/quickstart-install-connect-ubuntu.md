---
title: Introduzione a SQL Server 2017 in Ubuntu | Documenti Microsoft
description: Questa Guida introduttiva viene illustrato come installare SQL Server 2017 in Ubuntu e quindi creare query in un database con sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Active
ms.openlocfilehash: fd3b175cd8440d17da0f341cd13f65bb044f45a0
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Guida introduttiva: Installare SQL Server e creare un database in Ubuntu

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa Guida rapida, installare innanzitutto 2017 di SQL Server in Ubuntu 16.04. Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede input dell'utente e una connessione internet. Se si è interessati di [automatica](sql-server-linux-setup.md#unattended) o [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre di un computer con Ubuntu 16.04 **almeno 2 GB** di memoria.

Per installare Ubuntu sul proprio computer, visitare [ http://www.ubuntu.com/download/server ](http://www.ubuntu.com/download/server). È anche possibile creare macchine virtuali Ubuntu in Azure. Vedere [creare e gestire le macchine virtuali Linux con l'interfaccia CLI di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> In questo momento, il [sottosistema Windows per Linux](https://msdn.microsoft.com/commandline/wsl/about) per Windows 10 non è supportata come destinazione di installazione.

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installazione di SQL Server

Per configurare SQL Server in Ubuntu, eseguire i comandi seguenti in un terminal per installare il **mssql server** pacchetto.

> [!IMPORTANT]
> Se si è precedentemente installato una versione CTP o candidata di SQL Server 2017, è innanzitutto necessario rimuovere il repository precedente prima di registrare uno degli archivi di GA. Per ulteriori informazioni, vedere [modificare repository dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md).

1. Importare le chiavi GPG archivio pubblico:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrare il repository di Microsoft SQL Server Ubuntu:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > Questo è il repository di aggiornamento cumulativo (CU). Per ulteriori informazioni sulle opzioni di repository e le differenze, vedere [configurare repository per SQL Server in Linux](sql-server-linux-change-repo.md).

1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. Dopo il completamento dell'installazione del pacchetto, eseguire **installazione mssql conf** e seguire le istruzioni per impostare la password dell'account SA e scegliere l'edizione.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Se si sta tentando 2017 di SQL Server in questa esercitazione, sono liberamente concessi in licenza le seguenti edizioni: Evaluation, Developer ed Express.

   > [!NOTE]
   > Assicurarsi di specificare una password complessa per l'account SA (caratteri di lunghezza 8 minimo, incluse le lettere maiuscole e lettere minuscole, cifre in base 10 e/o i simboli non alfanumerici).

1. Al termine della configurazione, verificare che il servizio sia in esecuzione:

   ```bash
   systemctl status mssql-server
   ```

1. Se si prevede di connettersi in remoto, è anche necessario aprire la porta TCP di SQL Server (valore predefinito 1433) nel firewall.

A questo punto, SQL Server è in esecuzione nel computer Ubuntu ed è pronto per l'uso!

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. I passaggi seguenti installare gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

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

> [!TIP]
> **SQLCMD** è solo uno strumento per la connessione a SQL Server per eseguire query ed eseguire attività di gestione e sviluppo. Altri strumenti includono:
>
> * [SQL Server Operations Studio (Preview)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Codice di Visual Studio](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (Preview)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
