---
title: Installare SQL Server Agent in Linux | Documenti Microsoft
description: In questo argomento viene descritto come installare SQL Server Agent in Linux.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 1f6f741a87a13e5b5bc8ba83741e86b065378bad
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-agent-on-linux"></a>Installare SQL Server Agent su Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

I passaggi seguenti installare SQL Server Agent (**mssql-server agent**) in Linux. Il [SQL Server Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) esegue i processi pianificati di SQL Server. Per informazioni sulle funzionalità supportate per questa versione di SQL Server Agent, vedere il [note sulla versione](sql-server-linux-release-notes.md).

> [!NOTE]
> Prima di installare SQL Server Agent, innanzitutto [installare SQL Server RC2 +](sql-server-linux-setup.md#platforms). Ciò consente di configurare le chiavi e il repository in uso quando si installa il **mssql-server agent** pacchetto.

Installare SQL Server Agent per la piattaforma:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Installare su RHEL</a>

Utilizzare la procedura seguente per installare il **mssql-server agent** su Red Hat Enterprise Linux. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Se si dispone già di **mssql-server agent** installato, è possibile aggiornare la versione più recente con i comandi seguenti:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'argomento [installazione di SQL Server](sql-server-linux-setup.md#offline).

## <a name="ubuntu">Installare in Ubuntu</a>

Utilizzare la procedura seguente per installare il **mssql-server agent** in Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Se si dispone già di **mssql-server agent** installato, è possibile aggiornare la versione più recente con i comandi seguenti:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'argomento [installazione di SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Installare in SLES</a>

Utilizzare la procedura seguente per installare il **mssql-server agent** in SUSE Linux Enterprise Server. 

Installare **mssql-server agent** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Se si dispone già di **mssql-server agent** installato, è possibile aggiornare la versione più recente con i comandi seguenti:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'argomento [installazione di SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Passaggi successivi
Per ulteriori informazioni sull'utilizzo di SQL Server Agent per creare, pianificare ed eseguire processi, vedere [eseguire un processo di agente SQL Server in Linux](sql-server-linux-run-sql-server-agent-job.md).

