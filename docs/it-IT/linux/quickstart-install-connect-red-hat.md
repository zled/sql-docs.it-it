---
title: Introduzione a SQL Server 2017 su Red Hat Enterprise Linux | Documenti Microsoft
description: Questa Guida introduttiva viene illustrato come installare SQL Server 2017 in Red Hat Enterprise Linux e quindi creare query in un database con sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 0e4eb6995660ef1123055f6bc625486750d88829
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Guida introduttiva: Installare SQL Server e creare un database in Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa Guida rapida, installare innanzitutto 2017 di SQL Server su Red Hat Enterprise Linux (RHEL) 7.3 +. Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede input dell'utente e una connessione internet. Se si è interessati di [automatica](sql-server-linux-setup.md#unattended) o [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario avere un 7.3 RHEL o 7.4 macchina con **almeno 2 GB** di memoria.

Per installare Red Hat Enterprise Linux nel proprio computer, visitare [ http://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). È anche possibile creare macchine virtuali RHEL in Azure. Vedere [creare e gestire le macchine virtuali Linux con l'interfaccia CLI di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)e utilizzare `--image RHEL` nella chiamata a `az vm create`.

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installazione di SQL Server

Per configurare SQL Server su RHEL, eseguire i comandi seguenti in un terminal per installare il **mssql server** pacchetto:

> [!IMPORTANT]
> Se si è precedentemente installato una versione CTP o candidata di SQL Server 2017, è innanzitutto necessario rimuovere il repository precedente prima di registrare uno degli archivi di GA. Per ulteriori informazioni, vedere [modificare repository dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md).

1. Scaricare il file di configurazione di Microsoft SQL Server Red Hat repository:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Questo è il repository di aggiornamento cumulativo (CU). Per ulteriori informazioni sulle opzioni di repository e le differenze, vedere [configurare repository per SQL Server in Linux](sql-server-linux-change-repo.md).

1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo yum install -y mssql-server
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
   
1. Per consentire le connessioni remote, aprire la porta di SQL Server nel firewall su RHEL. La porta di SQL Server predefinita è TCP 1433. Se si utilizza **FirewallD** per il firewall, è possibile utilizzare i comandi seguenti:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

A questo punto, SQL Server è in esecuzione nel computer RHEL ed è pronto per l'uso.

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. I passaggi seguenti installare gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

1. Scaricare il file di configurazione di repository Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Se si dispone di una versione precedente di **mssql strumenti** installato, rimuovere tutti i pacchetti meno recenti di unixODBC.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Eseguire i comandi seguenti per installare **mssql strumenti** con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Per praticità, aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente. Ciò consente di eseguire gli strumenti senza specificare il percorso completo. Eseguire i comandi seguenti per modificare il **percorso** per entrambe le sessioni di accesso e/non-accesso interattivo:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
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
