---
title: La gestione di SQL Server in Linux | Documenti Microsoft
description: Questo articolo fornisce collegamenti a strumenti e attività comuni di gestione per SQL Server in esecuzione in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: sql-linux
ms.workload: On Demand
ms.openlocfilehash: de19f1952465c62bf026dbd3d92666b7a1b968ae
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Scegliere lo strumento appropriato per la gestione di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Esistono diversi modi per gestire 2017 di SQL Server in Linux. Nella sezione seguente fornisce una rapida panoramica di gestione diversi strumenti e tecniche con puntatori a ulteriori risorse.

## <a name="mssql-conf"></a>mssql-conf 
Il **mssql conf** strumento consente di configurare SQL Server in Linux. Per ulteriori informazioni, vedere [configurare SQL Server in Linux con mssql conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Quasi tutte le operazioni eseguite in uno strumento client può essere eseguita anche con istruzioni Transact-SQL. SQL Server fornisce [viste a gestione dinamica (DMV)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) di query che lo stato e configurazione di SQL Server. Sono inoltre disponibili [comandi Transact-SQL](https://msdn.microsoft.com/library/bb510741.aspx) per attività di gestione di database. È possibile eseguire questi comandi in qualsiasi strumento client che supporta la connessione a SQL Server e l'esecuzione di query Transact-SQL, ad esempio [sqlcmd](sql-server-linux-setup-tools.md) o [codice di Visual Studio](sql-server-linux-develop-use-vscode.md).

## <a name="sql-server-operations-studio-preview"></a>SQL Server operazioni Studio (anteprima)

Nuovo Microsoft SQL Operations Studio (preview) è uno strumento multipiattaforma per la gestione di SQL Server. Per ulteriori informazioni, vedere [Microsoft SQL Operations Studio (preview)](../sql-operations-studio/what-is.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio in Windows

SQL Server Management Studio (SSMS) è un'applicazione Windows che fornisce un'interfaccia utente grafica per la gestione di SQL Server. Anche se è attualmente in esecuzione solo in Windows, è possibile utilizzare, connettersi in remoto a istanze di SQL Server di Linux. Per ulteriori informazioni sull'utilizzo di SQL Server Management Studio per gestire SQL Server, vedere [utilizzare SSMS per gestire SQL Server in Linux](sql-server-linux-manage-ssms.md).

## <a name="mssql-cli-preview"></a>mssql-cli (preview)

Microsoft ha rilasciato un nuovo strumento di scripting multipiattaforma per SQL Server, [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/). Questo strumento è attualmente in anteprima.

## <a name="powershell"></a>PowerShell

PowerShell fornisce un ambiente completo della riga di comando per la gestione di SQL Server in Linux. Per ulteriori informazioni, vedere [utilizzare PowerShell per la gestione di SQL Server in Linux](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su SQL Server in Linux, vedere [SQL Server in Linux](sql-server-linux-overview.md).
