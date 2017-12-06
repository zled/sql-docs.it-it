---
title: Le funzioni RevoScaleR per l'utilizzo di dati di SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 5f3c9864-9c75-4688-947d-0940045b2671
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 36795d4813de07e21f7d89e1bfb59862498d3ce5
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="revoscaler-functions-for-working-with-sql-server-data"></a>Funzioni RevoScaleR per l'utilizzo di dati di SQL Server

In questo argomento viene fornita una panoramica delle funzioni principali forniti in RevoScaleR per lavorare con dati di SQL Server.

Per un elenco completo di funzioni ScaleR e sul loro utilizzo, vedere il [Microsoft R Server](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) riferimento.

## <a name="create-sql-server-data-sources"></a>Creare origini dati di SQL Server

Le funzioni seguenti consentono di definire un'origine dati di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Un oggetto origine dati è un contenitore che specifica una stringa di connessione con il set di dati desiderato, definito come tabella, vista o query. Le chiamate di stored procedure non sono supportate.

+ [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) -definire un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] oggetto origine dati.

+ [RxOdbcData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxodbcdata) -creare oggetti di dati per gli altri database ODBC. 

## <a name="perform-ddl-statements"></a>Eseguire istruzioni DDL

È possibile eseguire istruzioni DDL da R, se si hanno le autorizzazioni necessarie per l'istanza e database. Le funzioni seguenti utilizzano chiamate ODBC per eseguire istruzioni DDL o recuperare lo schema del database.

+ `rxSqlServerTableExists`e [rxSqlServerDropTable](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdroptable) -eliminare un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] tabella oppure verificare l'esistenza di un oggetto o tabella di database

+ [rxExecuteSQLDDL](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexecutesqlddl) -eseguire un comando di definizione del linguaggio DDL (Data) che definisce o modifica gli oggetti di database. Questa funzione non può restituire dati e viene utilizzata solo per recuperare o modificare i metadati dello schema dell'oggetto.

## <a name="define-or-manage-compute-contexts"></a>Definire o gestire contesti di calcolo

Le funzioni seguenti consentono di definire un nuovo contesto di calcolo, cambiare il contesto di calcolo o identificare il contesto di calcolo corrente.

+ [RxComputeContext](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxcomputecontext) - Crea un contesto di calcolo.

+ [rxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) - Genera un contesto di calcolo di SQL Server che consente l'esecuzione di funzioni **ScaleR** in SQL Server R Services. Questo contesto di calcolo è attualmente supportato solo per le istanze di SQL Server in Windows.

+ `rxGetComputeContext`e [rxSetComputeContext](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetcomputecontext) - ottenere o impostare il contesto di calcolo attivo.

## <a name="move-data-and-transform-data"></a>Dati di spostamento e trasformazione di dati

Dopo aver creato un oggetto origine dati, è possibile utilizzare l'oggetto per caricare dati, la trasformazione dei dati o scrivere i nuovi dati nella destinazione specificata. A seconda delle dimensioni dei dati nell'origine, è anche possibile definire le dimensioni del batch come parte dell'origine dati e spostare i dati in blocchi.

+ [metodi di rxOpen](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxopen-methods) - controllare se un'origine dati è disponibile, aprire o chiudere un'origine dati, leggere i dati da un'origine, scrivere i dati di destinazione e chiudere un'origine dati

+ [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) -spostare i dati da un'origine dati in archiviazione di file o in un frame di dati.

+ [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) -trasformazione dei dati durante lo spostamento tra le origini dati.

Le funzioni seguenti possono essere utilizzate per creare un archivio dati locale nel formato con estensione XDF. Questo file può essere utile quando si usano più dati di quanto sia possibile trasferire dal database in un batch o più dati di quanto sia possibile archiviare in memoria.

Ad esempio, se si sposta regolarmente grandi quantità di dati da un database in una workstation locale, anziché query database più volte per ogni operazione di R, è possibile utilizzare il file con estensione XDF come un tipo di cache per salvare i dati in locale e quindi utilizzarli nell'area di lavoro R.

+ [RxXdfData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxxdfdata) -creare un oggetto dati con estensione XDF

+ [rxReadXdf](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxreadxdf) -legge i dati da un file con estensione XDF in un frame di dati

Per ulteriori informazioni sull'utilizzo di queste funzioni, incluso l'utilizzo di dati origini diverse dalle [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], vedere [Howto Guide per analisi dei dati in Microsoft R](https://docs.microsoft.com/r-server/r/how-to-introduction).
