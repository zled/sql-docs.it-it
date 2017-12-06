---
title: Salvare e caricare gli oggetti di R da SQL Server tramite ODBC | Documenti Microsoft
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 6ac2e971-6b4f-4c73-ba57-29c716abd057
caps.latest.revision: "8"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8bc94b0b93bfc19f521fc7748f484f72fd90d0d
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="save-and-load-r-objects-from-sql-server-using-odbc"></a>Salvare e caricare gli oggetti di R da SQL Server tramite ODBC

SQL Server R Services può archiviare oggetti R serializzati in una tabella e quindi caricare l'oggetto dalla tabella in base alle necessità, senza dover eseguire nuovamente il codice R o ripetere il training del modello. La possibilità di salvare gli oggetti R in un database è fondamentale per gli scenari di training e salvataggio di un modello e quindi per un uso successivo per l'assegnazione dei punteggi o l'analisi.

Per migliorare le prestazioni di questo passaggio critico, il pacchetto **RevoScaleR** ora include nuove funzioni di serializzazione e deserializzazione che migliorano notevolmente le prestazioni e archiviano l'oggetto in modo più compatto. In questo articolo vengono descritte queste funzioni e sul loro utilizzo.

## <a name="overview"></a>Panoramica

Il pacchetto **RevoScaleR** ora include nuove funzioni che rendono più semplice salvare gli oggetti R in SQL Server e quindi leggere gli oggetti dalla tabella di SQL Server. In generale, ogni chiamata di funzione utilizza un archivio di valore chiave semplice, in cui la chiave è il nome dell'oggetto, e il valore associato alla chiave è l'oggetto varbinary R da spostare in o all'esterno di una tabella.

Per salvare gli oggetti di R in SQL Server direttamente da un ambiente di R, è necessario:

+ stabilire una connessione a SQL Server utilizzando il *RxOdbcData* origine dati.
+ Chiamare le funzioni di nuovo tramite la connessione ODBC
+ Facoltativamente, è possibile specificare che l'oggetto non serializzato. Quindi, scegliere un nuovo algoritmo di compressione da usare invece l'algoritmo di compressione predefinito.

Per impostazione predefinita, qualsiasi oggetto chiamato da R per lo spostamento in SQL Server viene serializzato e compresso. Al contrario, quando si carica un oggetto da una tabella SQL Server da usare nel codice R, l'oggetto viene deserializzato e decompresso.

## <a name="list-of-new-functions"></a>Elenco delle nuove funzioni

- `rxWriteObject` scrive un oggetto R in SQL Server usando l'origine dati ODBC.

- `rxReadObject` legge un oggetto R da un database di SQL Server usando un'origine dati ODBC.

- `rxDeleteObject` elimina un oggetto R dal database di SQL Server specificato nell'origine dati ODBC. Se sono presenti più oggetti identificati dalla combinazione chiave/versione, vengono eliminati tutti.

- `rxListKeys` elenca tutti gli oggetti disponibili come coppie chiave-valore. Ciò consente di determinare i nomi e le versioni degli oggetti R.

Per informazioni dettagliate sulla sintassi di ogni funzione, usare la Guida di R. I dettagli sono disponibili anche nel [riferimento ScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

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
