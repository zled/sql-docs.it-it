---
title: Introduzione a SQL Server 2017 in SUSE Linux Enterprise Server | Documenti Microsoft
description: In questa esercitazione introduttiva viene illustrato come installare SQL Server 2017 in SUSE Linux Enterprise Server e quindi creare query in un database con sqlcmd.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.workload: On Demand
ms.openlocfilehash: decf9cf88ef38264900c129c2626761718065739
ms.sourcegitcommit: 085dd05d56afecbb454206ed8402cfbaa597cfbe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Installazione di SQL Server e creare un database in SUSE Linux Enterprise Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questa esercitazione introduttiva, installare innanzitutto 2017 di SQL Server in SUSE Linux Enterprise Server (SLES) v12 SP2. Connettiti con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede input dell'utente e una connessione internet. Se si è interessati di [automatica](sql-server-linux-setup.md#unattended) o [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre di una macchina di SP2 SLES v12 con **almeno 2 GB** di memoria. Il file system deve essere **XFS** o **EXT4**. Altri file System, ad esempio **BTRFS**, non sono supportati.

Per installare SUSE Linux Enterprise Server nel computer, accedere a [https://www.suse.com/products/server](https://www.suse.com/products/server). È anche possibile creare macchine virtuali SLES in Azure. Vedere [creare e gestire le macchine virtuali Linux con l'interfaccia CLI di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)e utilizzare `--image SLES` nella chiamata a `az vm create`.

> [!NOTE]
> In questo momento, il [sottosistema Windows per Linux](https://msdn.microsoft.com/commandline/wsl/about) per Windows 10 non è supportata come destinazione di installazione.

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installazione di SQL Server

Per configurare SQL Server in SLES, eseguire i comandi seguenti in un terminal per installare il **mssql server** pacchetto:

> [!IMPORTANT]
> Se si è precedentemente installato una versione CTP o candidata di SQL Server 2017, è innanzitutto necessario rimuovere il repository precedente prima di registrare uno degli archivi di GA. Per ulteriori informazioni, vedere [modificare repository dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md).

1. Scaricare il file di configurazione di Microsoft SQL Server SLES repository:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   sudo zypper --gpg-auto-import-keys refresh
   ```

   > [!NOTE]
   > Questo è il repository di aggiornamento cumulativo (CU). Per ulteriori informazioni sulle opzioni di repository e le differenze, vedere [modificare repository del codice sorgente](sql-server-linux-setup.md#repositories).

1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo zypper install -y mssql-server
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

1. Se si prevede di connettersi in remoto, è anche necessario aprire la porta TCP di SQL Server (valore predefinito 1433) nel firewall. Se si utilizza il firewall SuSE, è necessario modificare il **/etc/sysconfig/SuSEfirewall2** file di configurazione. Modificare il **FW_SERVICES_EXT_TCP** voce per includere il numero di porta di SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

A questo punto, SQL Server è in esecuzione nel computer SLES ed è pronto per l'uso.

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. I passaggi seguenti installare gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

1. Aggiungere Zypper il repository di Microsoft SQL Server.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installare **mssql strumenti** con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Per praticità, aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente. Ciò consente di eseguire gli strumenti senza specificare il percorso completo. Eseguire i comandi seguenti per modificare il **percorso** per entrambe le sessioni di accesso e/non-accesso interattivo:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** è solo uno strumento per la connessione a SQL Server per eseguire query ed eseguire attività di gestione e sviluppo. Altri strumenti includono [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md) e [codice di Visual Studio](sql-server-linux-develop-use-vscode.md).

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
