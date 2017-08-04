---
title: Panoramica di SQL Server in Linux | Documenti Microsoft
description: In questo argomento viene descritto come SQL Server viene eseguita su Linux e fornisce informazioni su come per altre informazioni.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 1192afb7032f34f0af98c3c1051808e89dc22b63
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-on-linux"></a>SQL Server in Linux

Ora viene eseguito SQL Server in Linux. Questa versione più recente, SQL Server 2017 RC2, viene eseguito in Linux ed è in molti modi semplicemente a SQL Server. È lo stesso motore di database di SQL Server, molte funzionalità e i servizi indipendentemente dal sistema operativo simili.

## <a name="install"></a>Install

Per iniziare, installare SQL Server in Linux con una delle esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-docker.md)

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

