---
title: "Novità di SQL Server, 2017 in Linux | Documenti Microsoft"
description: "Questo argomento sono incluse nuove funzionalità per 2017 di SQL Server in Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 11/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.workload: On Demand
ms.openlocfilehash: cdc32cffd67c794f5ec2d04ac7410892475f4f7f
ms.sourcegitcommit: d122a41cc953ba3e269c8709a18aa84f7c17982c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2017
---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Novità di SQL Server 2017 su Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Questo articolo descrive le principali funzionalità e i servizi disponibili per SQL Server 2017 su Linux.

> [!NOTE]
> Oltre a queste funzionalità in questo articolo, gli aggiornamenti cumulativi vengono rilasciati a intervalli regolari dopo il rilascio GA. Questi aggiornamenti cumulativi forniscono numerosi miglioramenti e correzioni. Per informazioni sulla versione di aggiornamento Cumulativo più recente, vedere [http://aka.ms/sql2017cu](http://aka.ms/sql2017cu). Per il download del pacchetto e problemi noti, vedere il [note sulla versione](sql-server-linux-release-notes.md).

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
  - [Log shipping](sql-server-linux-use-log-shipping.md)

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

Per altre informazioni su SQL Server in Linux, vedere il [Panoramica](sql-server-linux-overview.md). Per i download del pacchetto e un elenco di funzionalità non supportate e i problemi noti, vedere il [note sulla versione](sql-server-linux-release-notes.md).

Per altri miglioramenti introdotti in SQL Server 2017, vedere [novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
