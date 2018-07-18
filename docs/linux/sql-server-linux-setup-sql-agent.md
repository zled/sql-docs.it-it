---
title: Installare SQL Server Agent in Linux | Documenti Microsoft
description: In questo articolo viene descritto come installare SQL Server Agent in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: eae6d3389405f6c70e486d0569a65ca5d0a0d15d
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34323402"
---
# <a name="install-sql-server-agent-on-linux"></a>Installare SQL Server Agent su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 Il [SQL Server Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) esegue i processi pianificati di SQL Server. A partire da SQL Server 2017 CU4, SQL Server Agent è incluso il **mssql server** pacchetto e viene disabilitata per impostazione predefinita. Per informazioni sulle funzionalità supportate per questa versione di SQL Server Agent insieme a informazioni sulla versione, vedere il [note sulla versione](sql-server-linux-release-notes.md).

 Installare SQL Server Agent:
- [Per le versioni 2017 CU4 e versioni successive, abilitare SQL Server Agent](#EnableAgentAfterCU4)
- [Per le versioni 2017 CU3 e versioni precedenti, installare SQL Server Agent](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Per le versioni 2017 CU4 e versioni successive, abilitare SQL Server Agent</a>

 Per abilitare SQL Server Agent, attenersi alla procedura seguente.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Se si esegue l'aggiornamento da 2017 CU3 o seguito con l'agente installato, SQL Server Agent verrà abilitata automaticamente e quella precedente verranno disinstallati pacchetti dell'agente.  

## <a name="InstallAgentBelowCU4">Per le versioni 2017 CU3 e versioni precedenti, installare SQL Server Agent</a>

> [!NOTE]
> Le istruzioni di installazione seguenti si applicano a SQL Server versioni 2017 CU3 e sotto. Prima di installare SQL Server Agent, innanzitutto [installare SQL Server 2017](sql-server-linux-setup.md#platforms). Ciò consente di configurare le chiavi e il repository in uso quando si installa il **mssql-server agent** pacchetto.

Installare SQL Server Agent per la piattaforma:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Installare su RHEL</a>

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

### <a name="ubuntu">Installare in Ubuntu</a>

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

### <a name="SLES">Installare in SLES</a>

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

Se occorre un'installazione offline, individuare il download del pacchetto in SQL Server Agent di [note sulla versione](sql-server-linux-release-notes.md). Quindi utilizzare gli stessi passaggi di installazione offline descritti nell'articolo [installazione di SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Passaggi successivi
Per ulteriori informazioni sull'utilizzo di SQL Server Agent per creare, pianificare ed eseguire processi, vedere [eseguire un processo di agente SQL Server in Linux](sql-server-linux-run-sql-server-agent-job.md).
