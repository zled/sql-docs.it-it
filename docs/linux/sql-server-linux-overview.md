---
title: Panoramica di SQL Server in Linux | Documenti Microsoft
description: In questo argomento viene descritto come SQL Server viene eseguita su Linux e fornisce informazioni su come per altre informazioni.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.openlocfilehash: 9cf216249d8e5971eb480e79bf9d97756cb3d948
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sql-server-on-linux"></a>SQL Server in Linux

SQL Server 2017 viene ora eseguito in Linux. È lo stesso motore di database di SQL Server, molte funzionalità e i servizi indipendentemente dal sistema operativo simili.

## <a name="install"></a>Install

Per iniziare, installare SQL Server in Linux con una delle esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker stesso viene eseguito su più piattaforme, il che significa che è possibile eseguire l'immagine di Docker in Windows, Mac e Linux.

## <a name="connect"></a>Connect

Dopo l'installazione, connettersi all'istanza di SQL Server nel computer Linux. È possibile connettersi in locale o in modalità remota e con un'ampia gamma di strumenti e i driver. Le esercitazioni di Guida introduttiva viene illustrato come utilizzare il [sqlcmd](sql-server-linux-setup-tools.md) strumento da riga di comando. Altri strumenti comprendono quanto segue:

| Strumento | Esercitazione |
|-----|-----|
| Codice di Visual Studio (codice di Visual Studio) | [Usare il codice di Visual Studio con SQL Server in Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Utilizzare SQL Server Management Studio in Windows per connettersi a SQL Server in Linux](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [Usare SSDT con SQL Server in Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Esplora

SQL Server 2017 ha lo stesso motore di database sottostanti in tutte le piattaforme supportate, tra cui Linux. Numero così elevato e le funzionalità esistenti funzionano nello stesso modo in Linux. Questa area della documentazione espone alcune di queste funzionalità da una prospettiva di Linux. Chiama anche le aree che sono previsti requisiti specifici in Linux.

Se si ha già familiarità con SQL Server, esaminare il [note sulla versione](sql-server-linux-release-notes.md) per linee guida generali e i problemi noti per questa versione. Esaminare quindi [novità di SQL Server in Linux](sql-server-linux-whats-new.md) nonché [novità di SQL Server 2017 generale](../sql-server/what-s-new-in-sql-server-2017.md).

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) Coinvolgimento del team di progettazione di SQL Server

- [DBA Stack Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): porre domande di amministrazione di database
- [Overflow dello stack](http://stackoverflow.com/questions/tagged/sql-server): porre domande di sviluppo
- [Forum MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): porre domande tecniche
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): i bug e funzionalità di richiesta Report
- [Reddit](https://www.reddit.com/r/SQLServer/): discutere di SQL Server
