---
title: Introduzione a SQL Server 2017 su SUSE Linux Enterprise Server | Microsoft Docs
description: Questa Guida introduttiva illustra come installare SQL Server 2017 su SUSE Linux Enterprise Server e quindi creare ed eseguire query di un database con sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: 77dd13139eba88a40cbf20094b880c5046ebfb05
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38057630"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Guida introduttiva: Installare SQL Server e creare un database su SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa Guida introduttiva, è prima di tutto installare SQL Server 2017 in SUSE Linux Enterprise Server (SLES) 12 SP2. Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede l'input dell'utente e una connessione a internet. Se è interessati al [automatica](sql-server-linux-setup.md#unattended) oppure [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [informazioni aggiuntive sull'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre di un SLES 12 SP2 computer con **almeno 2 GB** di memoria. Il file system deve essere **XFS** oppure **EXT4**. Altri file System, ad esempio **BTRFS**, non sono supportati.

Per installare SUSE Linux Enterprise Server nel proprio computer, visitare [ https://www.suse.com/products/server ](https://www.suse.com/products/server). È anche possibile creare macchine virtuali SLES in Azure. Visualizzare [creare e gestire VM Linux con Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)e usare `--image SLES` nella chiamata a `az vm create`.

> [!NOTE]
> A questo punto, il [sottosistema Windows per Linux](https://msdn.microsoft.com/commandline/wsl/about) per Windows 10 non è supportato come destinazione di installazione.

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installare SQL Server

Per configurare SQL Server in SLES, eseguire i comandi seguenti in un terminale per installare il **mssql-server** pacchetto:

> [!IMPORTANT]
> Se è stato precedentemente installato una versione CTP o RC di SQL Server 2017, è necessario rimuovere prima il repository precedente prima di registrare uno dei repository GA. Per altre informazioni, vedere [modificare i repository dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md).

1. Scaricare il file di configurazione del repository di Microsoft SQL Server SLES:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Questo è il repository di aggiornamenti cumulativi (CU). Per altre informazioni sulle opzioni di repository e le relative differenze, vedere [configurare i repository per SQL Server in Linux](sql-server-linux-change-repo.md).

1. Aggiornare i repository.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo zypper install -y mssql-server
   ```

1. Dopo il completamento dell'installazione del pacchetto, eseguire **mssql-conf setup** e seguire le istruzioni per impostare la password account SA e scegliere l'edizione.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Se si tenta di SQL Server 2017 in questa esercitazione, sono liberamente concessi in licenza seguenti edizioni: Evaluation, Developer ed Express.

   > [!NOTE]
   > Assicurarsi di specificare una password complessa per l'account SA (caratteri di lunghezza 8 minimo, incluse le lettere maiuscole e lettere minuscole, cifre in base 10 e/o i simboli non alfanumerici).

1. Al termine della configurazione, verificare che il servizio sia in esecuzione:

   ```bash
   systemctl status mssql-server
   ```

1. Se si prevede di connettersi in remoto, si potrebbe essere necessario anche aprire la porta TCP di SQL Server (valore predefinito 1433) nel firewall. Se si usa il firewall di SuSE, è necessario modificare il **/etc/sysconfig/SuSEfirewall2** file di configurazione. Modificare il **FW_SERVICES_EXT_TCP** voce da includere il numero di porta di SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

A questo punto, SQL Server è in esecuzione nel computer SLES ed è pronto per l'uso.

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. La procedura seguente installa gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

1. Aggiungere il repository di Microsoft SQL Server Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installare **mssql-tools** con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Per praticità, aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente. Ciò consente di eseguire gli strumenti senza specificare il percorso completo. Eseguire i comandi seguenti per modificare la **percorso** per sessioni di accesso e le sessioni interattive/senza accesso:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** è solo uno strumento per la connessione a SQL Server per eseguire query ed eseguire attività di gestione e sviluppo. Altri strumenti comprendono:
>
> * [SQL Server Operations Studio (Preview)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-manage-ssms.md)
> * [Visual Studio Code](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (Preview)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
