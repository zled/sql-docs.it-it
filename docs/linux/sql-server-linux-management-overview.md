---
title: La gestione di SQL Server in Linux | Documenti Microsoft
description: "In questo argomento vengono forniti collegamenti a strumenti e attività comuni di gestione per SQL Server in esecuzione in Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 5f7c0f61cf9f441c56529ddaaddc96a0c318ce59
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Scegliere lo strumento appropriato per la gestione di SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Esistono diversi modi per gestire SQL Server 2017 RC2 in Linux. Nella sezione seguente fornisce una rapida panoramica di gestione diversi strumenti e tecniche con puntatori a ulteriori risorse.

## <a name="mssql-conf"></a>MSSQL-conf 
Il **mssql conf** strumento consente di configurare SQL Server in Linux. Per ulteriori informazioni, vedere [configurare SQL Server in Linux con mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Quasi tutte le operazioni eseguite in uno strumento client può essere eseguita anche con istruzioni Transact-SQL. SQL Server fornisce [viste a gestione dinamica (DMV)](/sql-docs/docs/relational-databases/system-dynamic-management-views/system-dynamic-management-views) di query che lo stato e configurazione di SQL Server. Sono inoltre disponibili [comandi Transact-SQL](https://msdn.microsoft.com/library/bb510741.aspx) per attività di gestione di database. È possibile eseguire questi comandi in qualsiasi strumento client che supporta la connessione a SQL Server e l'esecuzione di query Transact-SQL. Gli esempi includono [sqlcmd](sql-server-linux-setup-tools.md), [codice di Visual Studio](sql-server-linux-develop-use-vscode.md), e [SQL Server Management Studio](sql-server-linux-manage-ssms.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio in Windows

SQL Server Management Studio (SSMS) è un'applicazione Windows che fornisce un'interfaccia utente grafica per la gestione di SQL Server. Anche se è attualmente in esecuzione solo in Windows, è possibile utilizzare, connettersi in remoto a istanze di SQL Server di Linux. Per ulteriori informazioni sull'utilizzo di SQL Server Management Studio per gestire SQL Server, vedere [utilizzare SSMS per gestire SQL Server in Linux](sql-server-linux-manage-ssms.md).

## <a name="powershell"></a>PowerShell

PowerShell fornisce un ambiente completo della riga di comando per la gestione di SQL Server in Linux. Per ulteriori informazioni, vedere [utilizzare PowerShell per la gestione di SQL Server in Linux](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su SQL Server in Linux, vedere [SQL Server in Linux](sql-server-linux-overview.md).
