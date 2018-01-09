---
title: Pacchetti R installati con SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 2783d4ce6ca9cd25b41c1e658f5e3bf2a4f05f24
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="r-packages-installed-with-sql-server"></a>Pacchetti R installati con SQL Server

Questo articolo descrive i pacchetti R installati con SQL Server se si installa e abilitano le funzionalità di machine learning. In questo articolo viene anche descritto come gestire e visualizzare i pacchetti esistenti o aggiungere nuovi pacchetti a un'istanza di SQL Server.

**Si applica a:** SQL Server 2017 Machine Learning Services (In-Database), SQL Server 2016 R Services (In-Database)

## <a name="what-is-the-instance-library-and-where-is-it"></a>Che cos'è la libreria di istanza e in cui è?

Soluzioni R che viene eseguito in SQL Server è possono utilizzare solo i pacchetti installati nella libreria R predefinita associata all'istanza. Quando si installano le funzionalità di R in SQL Server, la libreria di pacchetti R si trova sotto la cartella di istanza.

+ Istanza predefinita *MSSQLSERVER* 

    SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016:`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ Istanza denominata *Istanzadenominatautente* 

    SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016:`C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

È possibile eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente di R.

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Alternatiely, è possibile utilizzare il nuovo [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) funzione, se l'esecuzione di sp\_eseguire\_esterno\_script direttamente nel computer di destinazione. La funzione non può restituire i percorsi di libreria per le connessioni remote.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
```

> [!NOTE]
> Se si utilizza l'associazione per l'aggiornamento dei componenti R in un'istanza, è possibile modificare il percorso alla libreria di istanza. Assicurarsi di verificare libreria in cui è utilizzata da SQL Server.

## <a name="r-packages-installed-with-sql-server"></a>Pacchetti R installati con SQL Server

Per impostazione predefinita l'oggetto R **base** pacchetti installati. Pacchetti di base includono le funzionalità di base fornite da pacchetti come `stats` e `utils`.

Installazione di R in SQL Server 2016 o SQL Server 2017 sempre include il **RevoScaleR** pacchetto e pacchetti avanzati correlati e i provider che supporta i contesti di calcolo remoto, streaming, l'esecuzione parallela di funzione rx, e molte altre funzionalità. Per aggiornare il pacchetto RevoScaleR, di utilizzare l'associazione per l'aggiornamento solo di machine learning componenti, patch o aggiornare l'istanza in una versione più recente di SQL Server.

+ Per una panoramica delle funzionalità di R avanzata, vedere [su Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ Per scaricare le librerie RevoScaleR in un computer client, installare [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>Autorizzazioni necessarie per l'installazione di pacchetti R

In SQL Server 2016, un amministratore deve installare i nuovi pacchetti di R a livello di istanza di un. 

SQL Server 2017 introdotte nuove funzionalità per la gestione e installazione del pacchetto:

+ È possibile utilizzare i comandi di R da un client remoto per installare i pacchetti con ambito privato o condiviso. Questa funzionalità richiede [Microsoft R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install) o [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), nonché privilegi dbo sull'istanza.
+ Database sono state aggiunte nuove funzionalità per supportare la gestione di pacchetti dagli amministratori di database senza utilizzare T-SQL. Queste funzionalità forniscono in futuro, gli amministratori di database con la possibilità di delegare la maggior parte dei facet della gestione dei pacchetti per gli utenti con privilegi.

Questa sezione descrive le autorizzazioni necessarie per installare e gestire i pacchetti per ogni versione.

+ SQL Server 2016 R Services (In-Database)

    Per installare un nuovo pacchetto R in un computer che esegue [!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)], è necessario disporre di diritti amministrativi nel computer. È l'attività di amministratore del database o un altro amministratore nel server per assicurarsi che tutti i pacchetti necessari siano installati nel [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] istanza.

    Se non si dispone dei privilegi di amministratore nel computer che ospita il [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] istanza, è possibile fornire informazioni l'amministratore installare i pacchetti R e fornire l'accesso a un repository di pacchetti sicura in pacchetti richiesto da utenti possono essere ottenuti.

+ SQL Server 2017 Machine Learning Services

    Se si è un amministratore nell'istanza di SQL Server, è possibile installare i nuovi pacchetti quando è necessario. Essere semplicemente accertarsi di utilizzare la libreria predefinita che viene associata all'istanza. Pacchetti installati in altre posizioni non è possibile eseguire quando viene chiamato da una stored procedure. Qualsiasi codice R che viene eseguita tramite SQL Server come un contesto di calcolo richiede inoltre che i pacchetti siano disponibili nella libreria di istanza.

    Questa versione include anche alcune nuove funzionalità utilizzata per supportare la gestione più semplice di pacchetto per gli amministratori di database in una versione successiva. Per il momento, è consigliabile continuare a installare pacchetti R in base a livello di istanza.

+ R Server (Standalone)

    È necessario diritti amministrativi per il computer per installare i nuovi pacchetti di R.

+ Altri ambienti client

    Se si sta installando un nuovo pacchetto R in un computer in uso come workstation di R e il computer **non** dispone di un'istanza di [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] installata, sono comunque necessari diritti amministrativi per il computer installare il pacchetto. Dopo aver installato il pacchetto, è possibile eseguirlo in locale.

## <a name="managing-or-viewing-installed-packages"></a>Gestisce o Visualizza i pacchetti installati

Sono disponibili più modi che è possibile ottenere un elenco completo dei pacchetti installati. Per ulteriori informazioni, vedere [determinare quali pacchetti vengono installati in SQL Server](determine-which-packages-are-installed-on-sql-server.md).
