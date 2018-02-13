---
title: Installare SQL Server Agent in Linux | Documenti Microsoft
description: In questo articolo viene descritto come installare SQL Server Agent in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.workload: On Demand
ms.openlocfilehash: 7db50a59a4a6ce9ab7aa416e4ac8d597449541b7
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="install-sql-server-agent-on-linux"></a>Installare SQL Server Agent su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

I passaggi seguenti installare SQL Server Agent (**mssql-server agent**) in Linux. Il [SQL Server Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) esegue i processi pianificati di SQL Server. Per informazioni sulle funzionalità supportate per questa versione di SQL Server Agent, vedere il [note sulla versione](sql-server-linux-release-notes.md).

> [!NOTE]
> Prima di installare SQL Server Agent, innanzitutto [installare SQL Server 2017](sql-server-linux-setup.md#platforms). Ciò consente di configurare le chiavi e il repository in uso quando si installa il **mssql-server agent** pacchetto.

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

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'articolo [installazione di SQL Server](sql-server-linux-setup.md#offline).

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

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'articolo [installazione di SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Installare in SLES</a>

Utilizzare la procedura seguente per installare il **mssql-server agent** in SUSE Linux Enterprise Server. 

Install **mssql-server-agent** 

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

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'articolo [installazione di SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Passaggi successivi
Per ulteriori informazioni sull'utilizzo di SQL Server Agent per creare, pianificare ed eseguire processi, vedere [eseguire un processo di agente SQL Server in Linux](sql-server-linux-run-sql-server-agent-job.md).
