---
title: "Salvare e caricare oggetti R da SQL Server tramite ODBC | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 6ac2e971-6b4f-4c73-ba57-29c716abd057
caps.latest.revision: 8
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Salvare e caricare oggetti R da SQL Server tramite ODBC
SQL Server R Services può archiviare oggetti R serializzati in una tabella e quindi caricare l'oggetto dalla tabella in base alle necessità, senza dover eseguire nuovamente il codice R o ripetere il training del modello. La possibilità di salvare gli oggetti R in un database è fondamentale per gli scenari di training e salvataggio di un modello e quindi per un uso successivo per l'assegnazione dei punteggi o l'analisi. 

Per migliorare le prestazioni di questo passaggio critico, il pacchetto **RevoScaleR** ora include nuove funzioni di serializzazione e deserializzazione che migliorano notevolmente le prestazioni e archiviano l'oggetto in modo più compatto. Inoltre, è possibile salvare gli oggetti R direttamente in SQL Server da un ambiente R, chiamando queste nuove funzioni su una connessione ODBC mediante *RxOdbcData*.

## <a name="overview"></a>Panoramica

Il pacchetto **RevoScaleR** ora include nuove funzioni che rendono più semplice salvare gli oggetti R in SQL Server e quindi leggere gli oggetti dalla tabella di SQL Server. Queste funzioni richiedono che venga stabilita una connessione a SQL Server usando l'origine dati *RxOdbcData*.

In generale, le chiamate alla funzione vengono modellate in base a un archivio valori chiave semplice, in cui la chiave è il nome dell'oggetto e il valore associato alla chiave è l'oggetto varbinary R da spostare all'interno o all'esterno della tabella. 

- Per impostazione predefinita, qualsiasi oggetto chiamato da R per lo spostamento in SQL Server viene serializzato e compresso. 
- Al contrario, quando si carica un oggetto da una tabella SQL Server da usare nel codice R, l'oggetto viene deserializzato e decompresso.
- Facoltativamente, è possibile specificare che l'oggetto non venga serializzato e che venga usato un nuovo algoritmo di compressione invece dell'algoritmo di compressione predefinito.


## <a name="new-functions"></a>Funzioni nuove

- `rxWriteObject` scrive un oggetto R in SQL Server usando l'origine dati ODBC. 

- `rxReadObject` legge un oggetto R da un database di SQL Server usando un'origine dati ODBC.

- `rxDeleteObject` elimina un oggetto R dal database di SQL Server specificato nell'origine dati ODBC. Se sono presenti più oggetti identificati dalla combinazione chiave/versione, vengono eliminati tutti.

- `rxListKeys` elenca tutti gli oggetti disponibili come coppie chiave-valore. Ciò consente di determinare i nomi e le versioni degli oggetti R.

Per informazioni dettagliate sulla sintassi di ogni funzione, usare la Guida di R. Saranno disponibili informazioni dettagliate nelle [informazioni di riferimento di ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) su MSDN.

## <a name="how-to-store-r-objects-in-sql-server-using-odbc"></a>Come archiviare gli oggetti R in SQL Server tramite ODBC

Questa procedura illustra come è possibile usare le nuove funzioni per creare un modello e salvarlo in SQL Server.

1. Impostare la stringa di connessione per SQL Server.
   ```R
   conStr <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. Creare un oggetto origine dati *rxOdbcData* in R usando la stringa di connessione.
   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr)
   ```

3. Eliminare la tabella se esiste già e non si vuole tenere traccia delle versioni precedenti degli oggetti.

   ```R
   if(rxSqlServerTableExists(ds@table, ds@connectionString)) {
       rxSqlServerDropTable(ds@table, ds@connectionString)
       }
   ```
   
4. Definire una tabella che può essere usata per archiviare oggetti binari.

   ```R
   ddl <- paste(" CREATE TABLE [", ds@table, "] 
      (","  [id] varchar(200) NOT NULL,
       "," [value] varbinary(max),
       "," CONSTRAINT unique_id UNIQUE (id))", 
       sep = "") 
   ```
5. Aprire la connessione ODBC per creare la tabella e quando l'istruzione DDL è stata completata, chiudere la connessione.

   ```R
    rxOpen(ds, "w") 
    rxExecuteSQLDDL(ds, ddl) 
    rxClose(ds)
    ```
6. Generare gli oggetti R che si vuole archiviare.

   ```R
   infertLogit <- rxLogit(case ~ age + parity + education + spontaneous + induced, 
     data = infert)
   ```
6. Usare l'oggetto *RxOdbcData* creato in precedenza per salvare il modello nel database.

   ```R
   rxWriteObject(ds, "logit.model", infertLogit)
   ```

## <a name="how-to-read-r-objects-from-sql-server-using-odbc"></a>Come leggere gli oggetti R da SQL Server tramite ODBC

Questa procedura illustra come è possibile usare le nuove funzioni per caricare un modello da SQL Server.

1. Impostare la stringa di connessione per SQL Server.

   ```R
   conStr2 <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. Creare un oggetto origine dati *rxOdbcData* in R usando la stringa di connessione.

   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr2)
   ```
3. Leggere il modello dalla tabella specificandone il nome di oggetto R.

   ```R
    infertLogit2 <- rxReadObject(ds, "logit.model")
   ```

## <a name="see-also"></a>Vedere anche

[Caratteristiche e attività di R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)
