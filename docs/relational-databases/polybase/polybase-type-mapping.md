---
title: Mapping dei tipi con PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9839c46f477fe31d29214eed10dce0d673c9fd00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732606"
---
# <a name="type-mapping-with-polybase"></a>Mapping dei tipi con PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive il mapping tra le origini dati esterne PolyBase e SQL Server. È possibile usare queste informazioni per definire correttamente le tabelle esterne con il comando Transact-SQL [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).

## <a name="overview"></a>Panoramica

Quando si crea una tabella esterna con PolyBase, le definizioni di colonna, inclusi i tipi di dati e il numero di colonne, devono corrispondere ai dati nei file esterni. In caso di mancata corrispondenza, le righe di file vengono rifiutate quando si eseguono query sui dati effettivi.  
  
Per le tabelle esterne che fanno riferimento a file in origini dati esterne, è necessario eseguire il mapping delle definizioni di colonna e di tipo allo schema esatto del file esterno. Quando si definiscono i tipi di dati che fanno riferimento ai dati archiviati in Hadoop/Hive, usare i mapping seguenti tra i tipi di dati SQL e Hive ed eseguire il cast del tipo in un tipo di dati SQL quando si effettua una selezione. Se non specificato diversamente, i tipi includono tutte le versioni di Hive.

> [!NOTE]  
> SQL Server non supporta il valore di dati Hive *infinity* in alcuna conversione. PolyBase avrà esito negativo con un errore di conversione del tipo di dati.

## <a name="hadoop-type-mapping-reference"></a>Informazioni di riferimento per i mapping dei tipi Hadoop

| Tipo di dati SQL | Tipo di dati .NET            | Tipo di dati Hive | Tipo di dati Hadoop/Java | Commenti                       |
| ------------- | ------------------------- | -------------- | --------------------- | ------------------------------ |
| TINYINT       | Byte                      | TINYINT        | ByteWritable          | Solo per numeri non firmati.     |
| SMALLINT      | Int16                     | SMALLINT       | ShortWritable         |
| INT           | Int32                     | INT            | IntWritable           |
| BIGINT        | Int64                     | BIGINT         | LongWritable          |
| bit           | Boolean                   | boolean        | BooleanWritable       |
| FLOAT         | Double                    | double         | DoubleWritable        |
| REAL          | Single                    | FLOAT          | FloatWritable         |
| money         | Decimal                   | double         | DoubleWritable        |
| SMALLMONEY    | Decimal                   | double         | DoubleWritable        |
| NCHAR         | String<br /><br /> Char[] | string         | text                  |
| NVARCHAR      | String<br /><br /> Char[] | string         | Text                  |
| char          | String<br /><br /> Char[] | string         | Text                  |
| varchar       | String<br /><br /> Char[] | string         | Text                  |
| BINARY        | Byte[]                    | BINARY         | BytesWritable         | Si applica a Hive 0.8 e versioni successive. |
| varbinary     | Byte[]                    | BINARY         | BytesWritable         | Si applica a Hive 0.8 e versioni successive. |
| Data          | DateTime                  | TIMESTAMP      | TimestampWritable     |
| smalldatetime | DateTime                  | TIMESTAMP      | TimestampWritable     |
| datetime2     | DateTime                  | TIMESTAMP      | TimestampWritable     |
| DATETIME      | DateTime                  | TIMESTAMP      | TimestampWritable     |
| time          | TimeSpan                  | TIMESTAMP      | TimestampWritable     |
| Decimal       | Decimal                   | Decimal        | BigDecimalWritable    | Si applica a Hive 0.11 e versioni successive. |

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="oracle-type-mapping-reference"></a>Informazioni di riferimento per i mapping dei tipi Oracle

| Tipo di dati Oracle              | Tipo SQL Server |
| ----------------------------- | --------------- |
| float                         | float           |
| Decimal                       | Decimal         |
| Int                           | Int             |
| Long                          | Ntext           |
| Binary Float                  | Real            |
| Char                          | Nchar           |
| Varchar2                      | nvarchar        |
| Raw                           | Varbinary       |
| Long Raw                      | image           |
| Bfile                         | image           |
| BLOB                          | image           |
| Clob                          | image           |
| Rowid                         | Varchar         |
| date                          | Datetime2       |
| Timestamp                     | Datetime2       |
| Timestamp with local time zone | Datetime2       |

### <a name="type-mismatch-float"></a>Non corrispondenza dei tipi (Float)

Oracle supporta la precisione a virgola mobile 126, inferiore rispetto alla precisione supportata da SQL Server (53). È quindi possibile il mapping diretto di **Float (1-53)**, ma per valori superiori si verifica una perdita di dati a causa di troncamento.

### <a name="type-mismatch-character-types"></a>Non corrispondenza dei tipi (tipi carattere)

Per i tipi come **Long** e **Bfile**, Oracle supporta dimensioni dei tipi di dati pari a 4 GB. SQL Server supporta dimensioni pari a 2 GB. In nodo analogo, per i tipi di dati Oracle **Blob** e **clob**, Oracle può supportare fino a 128 TB, mentre i tipi di SQL Server **LONGVARBINARY** o **WLONGVARBINARY** non possono supportare più di 2 GB. Il mapping dei tipi con un tipo di dati di dimensioni superiori a 2 GB può comportare il troncamento dei dati.  

### <a name="type-mismatch-timestamp"></a>Non corrispondenza dei tipi (Timestamp)

I tipi **Timestamp** e **Timestamp con fuso orario locale** in Oracle supportano la precisione in secondi frazionari 9. Il tipo DateTime2 di SQL Server supporta la precisione in secondi frazionari 7.

Inoltre, Simba mappa **Date**, **Timestamp** e **Timestamp with local time zone** al tipo ODBC **SQL_TIMESTAMP** e infine al tipo di SQL Server **Timestamp**. **Timestamp** è un ID di riga univoco generato automaticamente. In teoria, **SQL_TIMESTAMP** dovrebbe essere mappato al tipo di SQL Server **DateTime/DateTime2** o i tipi Oracle **Date**, **Timestamp** e **Timestamp with local time zone** dovrebbero essere mappati al tipo ODBC **SQL_TYPE_TIMESTAMP**.

### <a name="driver-configuration-option"></a>Opzione di configurazione del driver

Le dimensioni del buffer predefinite per le colonne **Long/LOB** è 1.024 KB (configurabile).

## <a name="mongo-type-mapping-reference"></a>Informazioni di riferimento per i mapping dei tipi Mongo

| Tipo di dati BSON     | Tipo SQL Server |
| ------------------ | --------------- |
| Double             | float           |
| String             | nvarchar        |
| Object             |
| Array              |
| Dati binari        | nvarchar        |
| ID dell'oggetto.          | nvarchar        |
| Boolean            | bit             |
| date               | Datetime2       |
| Intero a 32 bit     | Int             |
| Timestamp          | nvarchar        |
| Intero a 64 bit     | BigInt          |
| DBPointer          | nvarchar        |
| Javascript         | nvarchar        |
| Max Key            | nvarchar        |
| Min Key            | nvarchar        |
| Simbolo             | nvarchar        |
| Espressione regolare | nvarchar        |
| Non definito/NULL     | nvarchar        |

### <a name="javascript-with-scope"></a>JavaScript (con ambito)

Il driver restituisce il valore sotto forma di stringa che contiene "Javascript non supportato con ambito".

### <a name="type-mismatch-string"></a>Non corrispondenza dei tipi (stringa)

Le stringhe MongoDB vengono convertite nel tipo **SQL_WVARCHAR** con dimensioni di colonna predefinite pari a 255. Queste dimensioni di colonna sono regolabili come parte della configurazione del driver. Nonostante la possibilità di configurare, **SQL_WVARCHAR** o il tipo di SQL Server **Varchar** supporta solo al massimo 2 GB, mentre MongoDB consente l'archiviazione di dati fino a 4 GB. Ciò potrebbe causare il troncamento dei dati.

### <a name="mongodb-driver-options"></a>Opzioni per il driver MongoDB

- **Enable double buffering** (Abilita doppia memorizzazione nel buffer): selezionata per impostazione predefinita.
- **Documents to fetch per block** (Documenti da recuperare per blocco): valore predefinito 4096.
- **Expose strings as SQL_WVARCHAR** (Esponi stringhe come SQL_WVARCHAR): selezionata per impostazione predefinita. Se questa opzione è deselezionata, le stringhe vengono esposte come SQL_VARCHAR.
- **String column size** (Dimensioni colonne di tipo stringa): valore predefinito 255.
- **Expose Binary as SQL_LONGVARBINARY** (Esponi dati binari come SQL_LONGVARBINARY): selezionata per impostazione predefinita. Se questa opzione è deselezionata, il tipo binario viene esposto come SQL_VARBINARY.
- **Binary Column Size** (Dimensioni colonne di tipo binario): valore predefinito 32767.
- **Enable passdown** (Abilita passdown) : selezionata per impostazione predefinita.

### <a name="schema-related-driver-configurations"></a>Configurazioni del driver correlate allo schema

- **LoadMetadataTable**: impostazione predefinita dal database. Richiede al driver di caricare la definizione dello schema dal file JSON specificato.
- **LocalMetadataFile**: in caso di lettura da un file, è necessario specificare il percorso completo.
- **Metodo di campionamento**:  
  - **default forward** (predefinito in avanti): il driver campiona i dati dal primo record.
  - **backward** (indietro): il driver campiona i dati a partire dall'ultimo record.
- **SamplingLimit**: valore predefinito 100 (numero massimo di record che il driver può campionare per generare la definizione dello schema temporanea). Se impostata su 0, il driver campiona ogni documento.
- **SamplingStepSize**: valore predefinito 1 (intervallo per il campionamento dei record durante la scansione del database per generare la definizione dello schema temporanea). Ad esempio, se impostata su 2, vengono campionati un record sì e uno no nel database.

## <a name="teradata-type-mapping-reference"></a>Informazioni di riferimento per i mapping dei tipi Teradata

| Tipo di dati Teradata               | Tipo SQL Server |
| -------------------------------- | --------------- |
| Int                              | Int             |
| Small Int                        | SmallInt        |
| Big Int                          | BigInt          |
| Byte Int                         | TinyInt         |
| Decimal                          | Decimal         |
| float                            | float           |
| Byte                             | Binario          |
| Varbyte                          | Varbinary       |
| BLOB                             | image           |
| Char                             | Nchar           |
| Clob                             | Ntext           |
| Varchar                          | nvarchar        |
| Graphic                          | Nchar           |
| JSON                             | Ntext           |
| Vargraphic                       | nvarchar        |
| date                             | date            |
| Time                             | Time            |
| Time with Time Zone              | Time            |
| Timestamp                        | Datetime2       |
| Interval Year                    |
| Interval year to month           |
| Interval Month                   |
| Interval Day                     |
| Interval Day to Hour             |
| Interval Day to Minute           |
| Interval Day to Second           |
| Interval Hour                    |
| Interval Hour to Minute          |
| Interval Hour to Second          |
| Interval Minute                  |
| Interval Minute to Second        |
| Interval Second                  |
| Period (DATE)                    |
| Period (TIME)                    |
| Period (TIME with Timezone)      |
| Period (Timestamp)               |
| Period (Timestamp with Timezone) |

### <a name="period-data-type"></a>Tipo di dati Period

Il tipo di dati **Period** rappresenta una durata contrassegnata da un limite di inizio e uno di fine. Essenzialmente, si tratta di una tupla. Non è disponibile alcun tipo equivalente di SQL Server per **Period**.

### <a name="time-with-time-zone-and-timestamp"></a>Time with Time Zone e Timestamp

I tipi **Time with Time Zone** e **Timestamp** contengono la differenza di fuso orario, persa durante la conversione. Questo problema può essere risolto mappando il tipo **SQL_Type_Time/SQL_Type_Timestamp** a **datetimeoffset** anziché a **Time/DateTime2**.

### <a name="byteint"></a>ByteInt

Simba esegue il mapping del tipo Teradata **ByteInt** che può contenere valori compresi tra 0 e 255 al tipo **TinyInt** che può contenere valori compresi tra -127 e 127. Ciò può comportare troncamenti.  

### <a name="clob"></a>CLOB

Il tipo di dati **CLOB** con set di caratteri **LATIN** deve essere in grado di accettare 2097088000 caratteri. Tuttavia, oltre 1073741823, le dimensioni del buffer diventano negative.  

### <a name="driver-configuration-options"></a>Opzioni di configurazione del driver

- Usare dati di tipo **DATE** per i parametri **TIMESTAMP**.
- Abilitare la modalità di catalogo personalizzato per le applicazioni 2.X.
- Restituire una stringa vuota nella colonna **CREATE_PARAMS** per **SQL_TIMESTAMP**.
- Restituire la lunghezza massima **CHAR/VARCHAR** come 32 KB.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come usare questa funzionalità, vedere l'articolo di riferimento per Transact-SQL per [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
