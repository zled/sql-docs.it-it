---
title: Novità di SQL Server, 2017 in Linux | Documenti Microsoft
description: In questo articolo evidenzia novità di SQL Server 2017 in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: 18b4fe2c83fbb1813fe2b8a63d74d72f8c71d0c7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Novità di SQL Server 2017 su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo descrive le principali funzionalità e i servizi disponibili per SQL Server 2017 su Linux.

> [!NOTE]
> Oltre a queste funzionalità in questo articolo, gli aggiornamenti cumulativi vengono rilasciati a intervalli regolari dopo il rilascio GA. che mettono a disposizione numerosi miglioramenti e diverse correzioni. Per informazioni sulla versione di aggiornamento Cumulativo più recente, vedere [ http://aka.ms/sql2017cu ](http://aka.ms/sql2017cu). Per il download del pacchetto e problemi noti, vedere il [note sulla versione](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>Motore di database di SQL Server

- Abilitare le funzionalità del motore di Database di SQL Server core.
- Supporto per i percorsi nativi di Linux.
- Supporto di IPv6.
- Supporto per file di database su NFS.
- Abilitato [trasparente Layer Security](sql-server-linux-encrypted-connections.md) crittografia (TLS).
- Abilitato [l'autenticazione di Active Directory](sql-server-linux-active-directory-authentication.md).
- [La funzionalità gruppi di disponibilità](sql-server-linux-availability-group-overview.md) per la disponibilità elevata.
- [Ricerca full-text](sql-server-linux-setup-full-text-search.md) supportano.

## <a name="sql-server-agent"></a>SQL Server Agent

- Abilitato [SQL Server Agent](sql-server-linux-setup-sql-agent.md) il supporto per le attività seguenti:
  - [Processi di Transact-SQL](sql-server-linux-run-sql-server-agent-job.md)
  - [Posta elettronica database](sql-server-linux-db-mail-sql-agent.md)
  - [Il log shipping](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Possibilità di eseguire pacchetti SSIS in Linux. Per ulteriori informazioni, vedere [configurare SQL Server Integration Services in Linux con ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Altri miglioramenti

- Strumento di configurazione della riga di comando [mssql conf](sql-server-linux-configure-mssql-conf.md).
- Supporto di installazione automatica con [le variabili di ambiente](sql-server-linux-configure-environment-variables.md).
- Multipiattaforma [estensione di Visual Studio Code mssql server](sql-server-linux-develop-use-vscode.md).
- Il generatore script multipiattaforma, [mssql scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Monitoraggio di vista a gestione dinamica (DMV) multipiattaforma, [strumento DBFS](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Passaggi successivi

Per installare SQL Server in Linux, utilizzare una delle seguenti esercitazioni:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

Per altri miglioramenti introdotti in SQL Server 2017, vedere [novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Per le risposte alle domande più frequenti, vedere il [SQL Server in domande frequenti su Linux](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
