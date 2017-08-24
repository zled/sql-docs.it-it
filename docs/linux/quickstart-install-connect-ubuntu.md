---
title: Introduzione a SQL Server 2017 in Ubuntu | Documenti Microsoft
description: In questa esercitazione introduttiva viene illustrato come installare SQL Server 2017 in Ubuntu e quindi creare query in un database con sqlcmd.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/24/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 052a2f0a7618c5e160d3c17a3a1efd7d7a4b3fd6
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-and-create-a-database-on-ubuntu"></a>Installazione di SQL Server e creare un database in Ubuntu

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

In questa esercitazione introduttiva, innanzitutto è necessario installare SQL Server 2017 RC2 in Ubuntu 16.04. Connettiti con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede input dell'utente e una connessione internet. Se si è interessati di [automatica](sql-server-linux-setup.md#unattended) o [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre di un computer con Ubuntu **almeno 3,25 GB** di memoria.

Per installare Ubuntu sul proprio computer, accedere a [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server). È anche possibile creare macchine virtuali Ubuntu in Azure. Vedere [creare e gestire le macchine virtuali Linux con l'interfaccia CLI di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installazione di SQL Server

Per configurare SQL Server in Ubuntu, eseguire i comandi seguenti in un terminal per installare il **mssql server** pacchetto.

1. Importare le chiavi GPG archivio pubblico:

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrare il repository di Microsoft SQL Server Ubuntu:

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list)"
   ```

1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. Dopo il completamento dell'installazione del pacchetto, eseguire **installazione mssql conf** e seguire le istruzioni per impostare la password dell'amministratore di sistema e si è scelto l'edizione.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Assicurarsi di specificare una password complessa per l'account SA (caratteri di lunghezza 8 minimo, incluse le lettere maiuscole e lettere minuscole, cifre in base 10 e/o i simboli non alfanumerici).

   > [!TIP]
   > Quando si installa RC2, licenze acquistate non deve provare a eseguire una delle edizioni. Poiché si tratta di una versione finale candidata, indipendentemente dall'edizione selezionato viene visualizzato il messaggio seguente:
   >
   > `This is an evaluation version.  There are [175] days left in the evaluation period.`
   >
   > Questo messaggio non riflette l'edizione selezionata. Si riferisce al periodo di anteprima per RC2.

1. Al termine della configurazione, verificare che il servizio sia in esecuzione:

   ```bash
   systemctl status mssql-server
   ```

1. Se si prevede di connettersi in remoto, è anche necessario aprire la porta TCP di SQL Server (valore predefinito 1433) nel firewall.

A questo punto, SQL Server è in esecuzione nel computer Ubuntu ed è pronto per l'uso!

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. I passaggi seguenti installare gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

1. Importare le chiavi GPG archivio pubblico:

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrare il repository Microsoft Ubuntu:

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
   ```

1. Aggiornare l'elenco delle origini ed eseguire il comando di installazione con il pacchetto di sviluppo unixODBC:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-tools unixodbc-dev
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
