---
title: Sviluppo di applicazioni per SQL Server in Linux | Documenti Microsoft
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.custom: H1Hack27Feb2017
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: c83b105706916c193cb1a0bbf966ff64fb7bac05
ms.contentlocale: it-it
ms.lasthandoff: 10/02/2017

---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Come iniziare a sviluppare applicazioni destinate a SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

È possibile creare applicazioni che si connettono e utilizzano 2017 di SQL Server in Linux da una varietà di linguaggi di programmazione, ad esempio c#, Java, Node.js, PHP, Python, Ruby e C++. È inoltre possibile utilizzare Framework web più comuni e altri framework relazionale Mapping ORM (Object).

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

- [SQLCMD](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [MSSQL-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Passaggi successivi

Per iniziare, installare SQL Server in Linux con una delle esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)

