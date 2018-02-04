---
title: Sviluppo di applicazioni per SQL Server in Linux | Documenti Microsoft
description: 
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.workload: On Demand
ms.openlocfilehash: 9bfd1b4f30593fa6ae4d17ec92bfa0047ea751bc
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Come iniziare a sviluppare applicazioni destinate a SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

È possibile creare applicazioni che si connettono e utilizzano 2017 di SQL Server in Linux da una varietà di linguaggi di programmazione, ad esempio c#, Java, Node.js, PHP, Python, Ruby e C++. È inoltre possibile utilizzare Framework web più comuni e altri framework relazionale Mapping ORM (Object).

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> Queste stesse opzioni di sviluppo consentono anche di destinazione SQL Server su altre piattaforme. Le applicazioni possono essere destinati a SQL Server in esecuzione in locale o nel cloud, in Docker, Windows o Linux macOS. O è possibile scegliere come destinazione Database SQL di Azure e Azure SQL Data Warehouse.

## <a name="try-the-tutorials"></a>Provare le esercitazioni

Il modo migliore per iniziare e compilare applicazioni con SQL Server è la valutazione di per se stessi.

- Passare a [esercitazioni introduttive](http://aka.ms/sqldev).
- Selezionare la piattaforma di sviluppo e di lingua.
- Provare gli esempi di codice.

> [!TIP]
> Se si desidera sviluppare per SQL Server 2017 in Docker, esaminiamo il **macOS** esercitazioni.

## <a name="create-new-applications"></a>Creare nuove applicazioni

Se si crea una nuova applicazione, esaminare un elenco di [librerie di connettività](sql-server-linux-develop-connectivity-libraries.md) per un riepilogo dei connettori e popolari Framework disponibili per diversi linguaggi di programmazione.

## <a name="use-existing-applications"></a>Utilizzare le applicazioni esistenti

Se si dispone di un'applicazione di database esistente, è possibile modificare semplicemente la relativa stringa di connessione alla destinazione 2017 di SQL Server in Linux. Assicurarsi di conoscere il [problemi noti](sql-server-linux-release-notes.md) in SQL Server 2017 in Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Utilizzare gli strumenti SQL esistenti in Windows con SQL Server in Linux

Strumenti attualmente eseguiti su Windows, ad esempio SQL Server Management Studio, SSDT e PowerShell, funzionano anche con SQL Server 2017 in Linux. Anche se non vengono eseguiti in modo nativo in Linux, è comunque possibile gestire le istanze remote di SQL Server in Linux. 

Vedere gli argomenti seguenti per ulteriori informazioni:

- [SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [PowerShell SQL](sql-server-linux-manage-powershell.md)

> [!Note] 
> Assicurarsi che le versioni più recenti di questi strumenti si utilizza per risultati ottimali.

## <a name="use-new-sql-tools-for-linux"></a>Utilizzare nuovi strumenti SQL per Linux

È possibile utilizzare il nuovo [estensione mssql](https://aka.ms/mssql-marketplace) per [codice di Visual Studio](https://code.visualstudio.com) su Linux, macOS e Windows. Per una procedura dettagliata, vedere l'esercitazione seguente:

- [Usare Visual Studio Code](sql-server-linux-develop-use-vscode.md)

È inoltre possibile utilizzare nuovi strumenti della riga di comando che sono di tipo nativi per Linux. Questi strumenti comprendono quanto segue:

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Passaggi successivi

Per iniziare, installare SQL Server in Linux con una delle Guide rapide seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
