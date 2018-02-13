---
title: Esportare e importare un database in Linux | Documenti Microsoft
description: 
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
ms.technology: database-engine
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: sql-linux
ms.workload: On Demand
ms.openlocfilehash: 817fc0ae018ebb7999ad572c0f18ede943ff7090
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>Esportare e importare un database in Linux con SQL Server Management Studio o SqlPackage.exe in Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene illustrato come utilizzare [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) e [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx) per esportare e importare un database in SQL Server 2017 in Linux. SQL Server Management Studio e SqlPackage.exe sono applicazioni di Windows, pertanto usare questa tecnica quando si dispone di un computer Windows in grado di connettersi a un'istanza remota di SQL Server in Linux.

È sempre necessario installare e utilizzare la versione più recente di SQL Server Management Studio (SSMS), come descritto in [utilizzare SQL Server Management Studio in Windows per connettersi a SQL Server in Linux](sql-server-linux-develop-use-ssms.md)

> [!NOTE]
> Se si esegue la migrazione di un database da un'istanza di SQL Server a un altro, consiglia di utilizzare [Backup e ripristino](sql-server-linux-migrate-restore-database.md).

## <a name="export-a-database-with-ssms"></a>Esportare un database con SSMS

1. Avviare SSMS digitando **Microsoft SQL Server Management Studio** nelle finestre di casella di ricerca e quindi fare clic sull'app desktop.

    ![SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png) 

2. Connettersi al database di origine in Esplora oggetti. Il database di origine può essere in esecuzione in locale di Microsoft SQL Server o nel cloud, Linux, Windows o Docker e Database SQL di Azure o Azure SQL Data Warehouse.

3. Fare doppio clic su database di origine in Esplora oggetti, scegliere **attività**, fare clic su **Esporta applicazione livello dati...**

4. Esportazione guidata, fare clic su **Avanti**e quindi scegliere il **impostazioni** , configurare l'esportazione per salvare il file BACPAC in un'altra posizione un disco locale o in un blob di Azure.

5. Per impostazione predefinita, vengono esportati tutti gli oggetti nel database. Fare clic su di **scheda Avanzate** e scegliere gli oggetti di database che si desiderano esportare.

6. Fare clic su **Avanti** , quindi su **Fine**.

Il *. File BACPAC viene correttamente creato nel percorso che prescelto e si è pronti per l'importazione in un database di destinazione.

## <a name="import-a-database-with-ssms"></a>Importa un database con SSMS

1. Avviare SSMS digitando **Microsoft SQL Server Management Studio** nelle finestre di casella di ricerca e quindi fare clic sull'app desktop.

    ![SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png) 

2. Connettersi al server di destinazione in Esplora oggetti. Il server di destinazione può essere eseguito in locale di Microsoft SQL Server o nel cloud, in Linux, Windows o Docker e Database SQL di Azure o Azure SQL Data Warehouse.

3. Fare doppio clic su di **database** cartella in Esplora oggetti e fare clic su **Importa applicazione livello dati...**

4. Per creare il database del server di destinazione, specificare un file BACPAC dal disco locale oppure selezionare l'account di archiviazione di Azure e un contenitore a cui è stato caricato il file BACPAC.

5. Specificare il nuovo nome di database per il database. Se si sta importando un database nel Database SQL Azure, impostare l'edizione di SQL Database di Microsoft Azure (livello di servizio), dimensioni massime del database e l'obiettivo di servizio (livello di prestazioni).

6. Fare clic su **Avanti** e quindi fare clic su **fine** per importare il file BACPAC in un nuovo database nel server di destinazione.

Il *. File BACPAC viene importato per creare un nuovo database nel server di destinazione specificato.

## <a id="sqlpackage"></a> Opzione della riga di comando SqlPackage

È inoltre possibile utilizzare lo strumento della riga di comando di SQL Server Data Tools (SSDT), [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx), per esportare e importare file BACPAC.

Il comando di esempio seguente esporta un file BACPAC:

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

Usare il comando seguente per importare dati di schema e utente di database da un. File BACPAC:

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>Vedere anche
Per ulteriori informazioni sull'utilizzo di SQL Server Management Studio, vedere [utilizzare SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx). Per ulteriori informazioni su SqlPackage.exe, vedere il [la documentazione di riferimento di SqlPackage](https://msdn.microsoft.com/library/hh550080.aspx).
