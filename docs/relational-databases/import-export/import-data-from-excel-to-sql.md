---
title: Importare dati da Excel a SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.assetid: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 70a1fd4dbec68d22187585de69a1d603c39e259e
ms.openlocfilehash: 3a978076b9776b57ffc996404c5f7773d7cf9094
ms.contentlocale: it-it
ms.lasthandoff: 07/28/2017

---
# <a name="import-data-from-excel-to-sql-server-or-azure-sql-database"></a>Importare dati da Excel a SQL Server o al database SQL di Azure
Sono disponibili vari modi per importare dati da file di Excel a SQL Server o al database SQL di Azure.
-   Si possono importare i dati direttamente da Excel tramite l'Importazione/Esportazione guidata SQL Server, Integration Services (SSIS) o la funzione OPENROWSET. 
-   È possibile salvare i dati di Excel come testo e quindi usare l'istruzione BULK INSERT, BCP o Azure Data Factory. In questo articolo sono riepilogate le varie opzioni con collegamenti a istruzioni più dettagliate.

> [!NOTE]
> Una descrizione completa di strumenti e servizi complessi come Azure Data Factory o SSIS esula dagli scopi di questa panoramica. Per scoprire di più sulla soluzione a cui si è interessati, seguire i collegamenti per le esercitazioni e per altre informazioni.

## <a name="sql-server-import-and-export-wizard"></a>Importazione/Esportazione guidata SQL Server

È possibile importare i dati direttamente dai file di Excel seguendo le varie pagine di una procedura guidata. Facoltativamente, è possibile salvare le impostazioni di importazione/esportazione come pacchetto di SQL Server Integration Services (SSIS) che è possibile personalizzare e riutilizzare.

![Connettersi a un'origine dati Excel](media/excel-connection.png)

Per un esempio di come usare la procedura guidata per l'importazione da Excel a SQL Server, vedere [Get started with this simple example of the Import and Export Wizard](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md) (Iniziare con un semplice esempio dell'Importazione/Esportazione guidata).

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

Se si ha familiarità con SSIS e si preferisce non eseguire l'Importazione/Esportazione guidata di SQL Server, creare un pacchetto SSIS che usa Excel come origine e SQL Server come destinazione nel flusso di dati.

![Componenti del flusso di dati](media/excel-to-sql-data-flow.png)

Per altre informazioni su questi componenti di SSIS, vedere gli argomenti seguenti.
-   [Origine Excel](../../integration-services/data-flow/excel-source.md)
-   [Destinazione SQL Server](../../integration-services/data-flow/sql-server-destination.md)

Per istruzioni su come creare pacchetti SSIS, vedere l'esercitazione [Creazione di un pacchetto ETL](../../integration-services/ssis-how-to-create-an-etl-package.md).

## <a name="openrowset-and-linked-servers"></a>OPENROWSET e server collegati
> [!NOTE]
> Il provider ACE (in precedenza provider Jet) che si connette ai file di Excel è destinato all'uso interattivo sul lato client. Se si usa il provider ACE nel server, in particolare in processi automatizzati o processi in esecuzione in parallelo, si possono ottenere risultati imprevisti.

Importare i dati direttamente dai file di Excel usando la funzione `OPENROWSET` o `OPENDATASOURCE`. Questo utilizzo è noto come *query distribuita*.

Prima di eseguire una query distribuita, è necessario abilitare l'opzione di configurazione del server `ad hoc distributed queries`, come illustrato nell'esempio seguente. Per altre informazioni, vedere [Opzione di configurazione del server ad hoc distributed queries](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md).

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'Ad Hoc Distributed Queries', 1;
RECONFIGURE;
GO
```

L'esempio di codice seguente importa i dati dal foglio di lavoro di Excel `Customers` in una nuova tabella di SQL Server con `OPENROWSET`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENROWSET('Microsoft.ACE.OLEDB.12.0',
    'Excel 12.0; Database=D:\Desktop\Data.xlsx', [Data$]);
GO
```

Ecco lo stesso esempio con `OPENDATASOURCE`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENDATASOURCE('Microsoft.ACE.OLEDB.12.0',
    'Data Source=D:\Desktop\Data.xlsx;Extended Properties=Excel 12.0')...[Data$];
GO
```

Per *aggiungere* i dati importati a una tabella *esistente* invece di creare una nuova tabella, usare la sintassi `INSERT INTO ... SELECT ... FROM ...` al posto della sintassi `SELECT ... INTO ... FROM ...` usata negli esempi precedenti.

Per selezionare i dati di Excel senza importarli, usare semplicemente la sintassi `SELECT ... FROM ...`.

Per altre informazioni sulle query distribuite, vedere gli argomenti seguenti.
-   [Query distribuite](https://msdn.microsoft.com/library/ms188721(v=sql.105).aspx) (Le query distribuite sono ancora supportate in SQL Server 2016, ma la documentazione relativa a questa funzionalità non è stata aggiornata.)
-   [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)
-   [OPENDATASOURCE](../../t-sql/functions/openquery-transact-sql.md)

È anche possibile configurare una connessione permanente al file di Excel come *server collegato*. L'esempio seguente importa i dati dal foglio di lavoro `Data` nel server collegato di Excel esistente `EXCELLINK` in una nuova tabella di SQL Server denominata `Data_ls`.

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_ls FROM EXCELLINK...[Data$];
GO
```

È possibile creare un server collegato da SQL Server Management Studio o eseguendo la stored procedure di sistema `sp_addlinkedserver`, come illustrato nell'esempio seguente.

```sql
DECLARE @RC int

DECLARE @server     nvarchar(128)
DECLARE @srvproduct nvarchar(128)
DECLARE @provider   nvarchar(128)
DECLARE @datasrc    nvarchar(4000)
DECLARE @location   nvarchar(4000)
DECLARE @provstr    nvarchar(4000)
DECLARE @catalog    nvarchar(128)

-- Set parameter values
SET @server =     'EXCELLINK'
SET @srvproduct = 'Excel'
SET @provider =   'Microsoft.ACE.OLEDB.12.0'
SET @datasrc =    'D:\Desktop\Data.xlsx'
SET @provstr =    'Excel 12.0'

EXEC @RC = [master].[dbo].[sp_addlinkedserver] @server, @srvproduct, @provider,
@datasrc, @location, @provstr, @catalog
```

Per altre informazioni sui server collegati, vedere gli argomenti seguenti.
-   [Creare server collegati](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)
-   [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)

Per altri esempi e informazioni sia sui server collegati che sulle query distribuite, vedere gli argomenti seguenti.
-   [How to use Excel with SQL Server linked servers and distributed queries](https://support.microsoft.com/help/306397/how-to-use-excel-with-sql-server-linked-servers-and-distributed-queries) (Come usare Excel con server collegati e query distribuite di SQL Server)
-   [Come importare dati da Excel a SQL Server](https://support.microsoft.com/help/321686/how-to-import-data-from-excel-to-sql-server)

## <a name="prerequisite---save-excel-data-as-text"></a>Prerequisito - Salvare i dati di Excel come testo
Per usare i restanti metodi descritti in questa pagina, ovvero l'istruzione BULK INSERT, lo strumento BCP o Azure Data Factory, è prima di tutto necessario esportare i dati di Excel in un file di testo.

In Excel selezionare **File | Salva con nome** e quindi selezionare **Testo (con valori delimitati da tabulazioni) (\*.txt)** o **CSV (delimitato dal separatore di elenco) (\*.csv)** come tipo di file di destinazione.

> [!TIP]
> Per ottenere risultati ottimali con gli strumenti per l'importazione dei dati, salvare fogli che contengono solo le intestazioni di colonna e le righe di dati. Se i dati salvati contengono titoli di pagina, righe vuote, note e così via, possono verificarsi risultati imprevisti in un secondo momento quando si importano i dati.

## <a name="bulk-insert-command"></a>Comando BULK INSERT

`BULK INSERT` è un comando che è possibile eseguire da SQL Server Management Studio. L'esempio seguente carica i dati dal file con valori delimitati da virgole `Data.csv` in una tabella esistente.

```sql
USE ImportFromExcel;
GO
BULK INSERT Data_bi FROM 'D:\Desktop\data.csv'
   WITH (
      FIELDTERMINATOR = ',',
      ROWTERMINATOR = '\n'
);
GO
```

Per altre informazioni, vedere gli argomenti seguenti.
-   [Importare dati per operazioni bulk usando BULK INSERT o OPENROWSET (BULK...)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
-   [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)

## <a name="bcp-tool"></a>Strumento BCP

BCP è uno strumento di SQL Server eseguibile dal prompt dei comandi. L'esempio seguente carica i dati dal file CSV `Data.csv` nella tabella `Data_bcp` esistente in SQL Server.

```sql
bcp.exe ImportFromExcel..Data_bcp in "D:\Desktop\data.csv" -T -c -t ,
```

Per altre informazioni, vedere gli argomenti seguenti.
-   [Importare ed esportare dati per operazioni bulk usando l'utilità bcp](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
-   [Utilità bcp](../../tools/bcp-utility.md)
-   [Preparare i dati per l'importazione o l'esportazione bulk](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)

## <a name="copy-wizard-azure-data-factory"></a>Copia guidata (Azure Data Factory)
È possibile importare i dati salvati come file di testo seguendo le varie pagine di una procedura guidata. Per altre informazioni sulla Copia guidata, vedere gli argomenti seguenti.
-   [Copia guidata di Azure Data Factory](https://docs.microsoft.com/azure/data-factory/data-factory-azure-copy-wizard)
-   [Esercitazione: Creare una pipeline con l'attività di copia usando la Copia guidata di Data Factory](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-wizard-tutorial).

## <a name="azure-data-factory"></a>Azure Data Factory
Se si ha familiarità con Azure Data Factory e si preferisce non eseguire la Copia guidata di Azure Data Factory, creare una pipeline con un'attività di copia dal file di testo in un percorso di archiviazione di file a SQL Server o al database SQL di Azure.

Per altre informazioni sull'uso di questi sink e origini di Data Factory, vedere gli argomenti seguenti.
-   [File system](https://docs.microsoft.com/azure/data-factory/data-factory-onprem-file-system-connector)
-   [SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-sqlserver-connector)
-   [Database SQL di Azure](https://docs.microsoft.com/azure/data-factory/data-factory-azure-sql-connector)

Per istruzioni su come copiare dati con Azure Data Factory, vedere gli argomenti seguenti.
-   [Spostare dati con l'attività di copia](https://docs.microsoft.com/azure/data-factory/data-factory-data-movement-activities)
-   [Tutorial: Create a pipeline with Copy Activity using Azure portal](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-from-azure-blob-storage-to-sql-database) (Esercitazione: Creare una pipeline con l'attività di copia usando il portale di Azure)

