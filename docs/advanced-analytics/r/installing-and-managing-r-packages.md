---
title: Pacchetti R installati con SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6fa079ca7cb13a3fcae98c768f5961f59e5ec37f
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="r-packages-installed-with-sql-server"></a>Pacchetti R installati con SQL Server

In questo articolo vengono descritti i pacchetti R installati con SQL Server e fornisce informazioni su come gestire e visualizzare i pacchetti esistenti.

In questo articolo include anche collegamenti a informazioni sull'aggiunta di nuovi pacchetti per l'utilizzo con SQL Server.

**Si applica a:** SQL Server 2017 Machine Learning Services (In-Database), SQL Server 2016 R Services (In-Database)

## <a name="what-is-the-instance-library-and-where-is-it"></a>Che cos'è la libreria di istanza e in cui è?

Soluzioni R che viene eseguito in SQL Server è possono utilizzare solo i pacchetti installati nella libreria R predefinita associata all'istanza.

Quando si installano le funzionalità di R in SQL Server, la libreria di pacchetti R si trova sotto la cartella di istanza.

+ Istanza predefinita *MSSQLSERVER* 

    SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016:`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ Istanza denominata *Istanzadenominatautente* 

    SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016:`C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

È possibile eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente di R.

```SQL
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```
## <a name="r-packages-installed-with-sql-server"></a>Pacchetti R installati con SQL Server

Quando si installa il linguaggio R in SQL Server, per impostazione predefinita l'oggetto R **base** pacchetti installati. Pacchetti di base includono le funzionalità di base fornite da pacchetti come `stats` e `utils`.

L'installazione di R in SQL Server 2016 e SQL Server 2017 include inoltre il **RevoScaleR** pacchetto e pacchetti avanzati correlati e i provider che supporta i contesti di calcolo remoto, streaming, l'esecuzione parallela di funzione rx, e molte altre funzionalità.

+ Per una panoramica delle funzionalità di R avanzata, vedere [su Machine Learning Server](https://docs.microsoft.com/r-server/what-is-microsoft-r-server)

+ Per scaricare le librerie RevoScaleR in un computer client, installare [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>Autorizzazioni necessarie per l'installazione di pacchetti R

In SQL Server 2016, un amministratore deve installare i nuovi pacchetti di R a livello di istanza di un. In SQL Server 2017, sono state aggiunte nuove funzionalità di database l'amministratore del database che offrono la possibilità di delegare la gestione dei pacchetti agli utenti selezionati.

Questa sezione descrive le autorizzazioni necessarie per installare e gestire i pacchetti per ogni versione.

+ SQL Server 2016 R Services (In-Database)

    Per installare un nuovo pacchetto R in un computer che esegue [!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)], è necessario disporre di diritti amministrativi nel computer. È l'attività di amministratore del database o un altro amministratore nel server per assicurarsi che tutti i pacchetti necessari siano installati nel [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] istanza.

    Se non si dispone dei privilegi di amministratore nel computer che ospita il [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] istanza, è possibile fornire informazioni l'amministratore installare i pacchetti R e fornire l'accesso a un repository di pacchetti sicura in pacchetti richiesto da utenti possono essere ottenuti.

+ SQL Server 2017 Machine Learning Services

    Questa versione include funzioni di gestione dei pacchetti che consentono ad amministratori di database di delegare i diritti di installazione del pacchetto agli utenti selezionati. Se questa funzionalità è stata abilitata, richiedere che l'amministratore del database aggiunti a uno dei nuovi ruoli di pacchetto. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md).

    Se si è un amministratore nell'istanza di SQL Server, è possibile installare i nuovi pacchetti quando è necessario. Essere semplicemente accertarsi di utilizzare la libreria predefinita che viene associata all'istanza. Pacchetti installati in altre posizioni non è possibile eseguire quando viene chiamato da una stored procedure. Qualsiasi codice R che viene eseguita tramite SQL Server come un contesto di calcolo richiede inoltre che i pacchetti siano disponibili nella libreria di istanza.

+ R Server (Standalone)

    È necessario diritti amministrativi per il computer per installare i nuovi pacchetti di R.

+ Altri ambienti client

    Se si sta installando un nuovo pacchetto R in un computer in uso come workstation di R e il computer **non** dispone di un'istanza di [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] installata, sono comunque necessari diritti amministrativi per il computer installare il pacchetto. Dopo aver installato il pacchetto, è possibile eseguirlo in locale.

## <a name="managing-or-viewing-installed-packages"></a>Gestisce o Visualizza i pacchetti installati

Sono disponibili più modi che è possibile ottenere un elenco completo dei pacchetti installati. Per ulteriori informazioni, vedere [determinare quali pacchetti vengono installati in SQL Server](determine-which-packages-are-installed-on-sql-server.md).
