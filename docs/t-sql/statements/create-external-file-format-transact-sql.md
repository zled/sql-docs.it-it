---
title: CREARE un formato di FILE esterno (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL FILE FORMAT
- CREATE_EXTERNAL_FILE_FORMAT
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, file format
- PolyBase, external file format
ms.assetid: abd5ec8c-1a0e-4d38-a374-8ce3401bc60c
caps.latest.revision: 25
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab356583cb69cc6e98bacc2a6e28145887902043
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-file-format-transact-sql"></a>CREARE un formato di FILE esterno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Crea una definizione di formato di file esterno PolyBase per i dati esterni archiviati in Hadoop o archiviazione blob di Azure, archivio Azure Data Lake. Creazione di un formato di file esterno è un prerequisito per la creazione di una tabella esterna PolyBase. Tramite la creazione di un formato di file esterno, specificare il layout effettivo dei dati a cui fa riferimento una tabella esterna.  
  
 PolyBase supporta questi formati di file:  
  
-   Testo delimitato  
  
-   Hive RCFile  
  
-   Hive ORC  
  
-   Parquet  
  
 Per creare una tabella esterna, vedere [CREATE EXTERNAL TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-table-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Create an external file format for PARQUET files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = PARQUET  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.GzipCodec'      }  
    ]);  
  
--Create an external file format for ORC files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = ORC  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.DefaultCodec'      }  
    ]);  
  
--Create an external file format for RCFILE.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = {  
        'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
      | 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
    }  
    [ , DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec' ]);  
  
--Create an external file format for DELIMITED TEXT files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT  
    [ , FORMAT_OPTIONS ( <format_options> [ ,...n  ] ) ]  
    [ , DATA_COMPRESSION = {  
           'org.apache.hadoop.io.compress.GzipCodec'  
         | 'org.apache.hadoop.io.compress.DefaultCodec'  
        }  
     ]);  
  
<format_options> ::=  
{  
    FIELD_TERMINATOR = field_terminator  
    | STRING_DELIMITER = string_delimiter  
    | DATE_FORMAT = datetime_format  
    | USE_TYPE_DEFAULT = { TRUE | FALSE } 
    | Encoding = {'UTF8' | 'UTF16'} 
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *file_format_name*  
 Specifica un nome per il formato di file esterno.  
  
 FORMAT_TYPE  
 Specifica il formato dei dati esterni.  
  
 PARQUET  
 Specifica un formato Parquet.  
  
 ORC  
 Specifica un formato con ottimizzazione per la riga a colonne (ORC). Questa opzione richiede Hive 0.11 o versione successiva nel cluster Hadoop esterno. In Hadoop, il formato file ORC offre una migliore compressione e prestazioni rispetto al formato di file RCFILE.  
  
 RCFILE (in combinazione con SERDE_METHOD = *SERDE_method*)  
 Specifica un formato a colonne di Record (RcFile). Questa opzione richiede di specificare un serializzatore di Hive e metodo deserializzatore (SerDe). Questo requisito è lo stesso, se si utilizza Hive/HiveQL in Hadoop per eseguire query nei file RC. Si noti che il metodo SerDe viene fatta distinzione tra maiuscole e minuscole.  
  
 Esempi di specifica RCFile con i due metodi SerDe PolyBase supporta.  
  
-   FORMAT_TYPE = RCFILE, SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
  
-   FORMAT_TYPE = RCFILE, SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
  
 DELIMITEDTEXT  
 Specifica un formato di testo con i delimitatori di colonna, detto anche i caratteri di terminazione del campo.  
  
 FIELD_TERMINATOR = *field_terminator*  
 Si applica solo ai file di testo delimitato da virgole. Specifica uno o più caratteri che contrassegnano la fine di ogni campo (colonna) nel file di testo delimitato. Il valore predefinito è il ꞌ carattere pipe | ꞌ. Per il supporto garantito, è consigliabile utilizzare uno o più caratteri ascii.
  
  
 Esempi:  
  
-   FIELD_TERMINATOR = ' |'  
  
-   FIELD_TERMINATOR = ' '  
  
-   FIELD_TERMINATOR = ꞌ\tꞌ  
  
-   FIELD_TERMINATOR = "~ | ~'  
  
 STRING_DELIMITER = *string_delimiter*  
 Specifica il carattere di terminazione del campo per i dati di tipo stringa nel file di testo delimitato. Il delimitatore di stringa di uno o più caratteri ed è racchiuso tra virgolette. Il valore predefinito è una stringa vuota "". Per il supporto garantito, è consigliabile utilizzare uno o più caratteri ascii.
 
  
 Esempi:  

-   STRING_DELIMITER = ' "'

-   STRING_DELIMITER = '0x22' - hex le virgolette doppie
  
-   STRING_DELIMITER = ' *'  
  
-   STRING_DELIMITER = Ꞌ, Ꞌ  
  
-   STRING_DELIMITER = '0x7E0x7E' - due tildas (ad esempio ~ ~)
  
 DATE_FORMAT = *datetime_format*  
 Specifica un formato personalizzato per tutti i dati di data e ora che potrebbero essere visualizzati in un file di testo delimitato da virgole. Se il file di origine utilizza formati datefime predefiniti, questa opzione non è più necessaria. Solo il formato datetime personalizzato è consentito per ogni file. È possibile specificare più formati di data e ora personalizzate per ogni file. Tuttavia, è possibile utilizzare più formati di data/ora se ciascuna di esse è il formato predefinito per il tipo di dati corrispondente nella definizione della tabella esterna.
 
 
PolyBase utilizza solo il formato della data personalizzato per l'importazione dei dati. Non utilizza il formato personalizzato per la scrittura di dati in un file esterno.

 Quando DATE_FORMAT non è specificato o è una stringa vuota, PolyBase utilizzerà i formati predefiniti seguenti:  
  
-   DateTime: 'aaaa-MM-gg hh: mm:'  
  
-   SmallDateTime: "yyyy-MM-dd HH: mm"  
  
-   Data: 'aaaa-MM-GG'  
  
-   DateTime2: 'aaaa-MM-gg hh: mm:'  
  
-   DateTimeOffset: 'aaaa-MM-gg hh: mm:'  
  
-   Ora: 'hh'  
  
 **Formati di data di esempio** sono nella tabella seguente.  
  
 Note sulla tabella:  
  
-   Anno, mese e giorno può avere un'ampia gamma di formati e ordini. La tabella mostra solo AMG. Mese può contenere cifre 1 o 2 o 3 caratteri. Giorno può avere cifre 1 o 2. Anno può avere 2 o 4 cifre.  
  
-   Millisecondi (fffffff) non è necessaria.  
  
-   AM, pm (tt) non è obbligatorio. Il valore predefinito è AM.  
  
|Date (tipo)|Esempio|Description|  
|---------------|-------------|-----------------|  
|DateTime|DATE_FORMAT = 'aaaa-MM-gg hh'|Oltre a anno, mese e giorno, sono inclusi 00-24 ore, da 00 a 59 minuti, da 00 a 59 secondi e 3 cifre per i millisecondi.|  
|DateTime|DATE_FORMAT = 'aaaa-MM-gg hh:mm:ss.ffftt'|Oltre a anno, mese e giorno, sono inclusi 00-12 ore, da 00 a 59 minuti, da 00 a 59 secondi, 3 cifre per i millisecondi e AM, am, PM o pm.|  
|SmallDateTime|DATE_FORMAT = "yyyy-MM-dd HH: mm"|Oltre a anno, mese e giorno, sono inclusi 00 e 23 ore, da 00 a 59 minuti.|  
|SmallDateTime|DATE_FORMAT = 'aaaa-MM-gg hh:mmtt'|Oltre a anno, mese e giorno, sono inclusi 00-11 ore, minuti di 00 e 59, nessun secondi e AM, am, PM o pm.|  
|Data|DATE_FORMAT = "yyyy-MM-dd"|Anno, mese e giorno. Nessun elemento ora è incluso.|  
|Data|DATE_FORMAT = 'AAAA-MMM-GG'|Anno, mese e giorno. Se month è specificato con 3 M, il valore di input è in uno o le stringhe di gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre o Dec.|  
|datetime2|DATE_FORMAT = "aaaa-MM-GG fffffff"|Oltre a anno, mese e giorno, sono inclusi 00 e 23 ore, da 00 a 59 minuti, da 00 a 59 secondi e 7 cifre per i millisecondi.|  
|datetime2|DATE_FORMAT = 'aaaa-MM-gg hh:mm:ss.ffffffftt'|Oltre a anno, mese e giorno, sono inclusi 00-11 ore, da 00 a 59 minuti, da 00 a 59 secondi, di 7 cifre per i millisecondi e AM, am, PM o pm.|  
|DateTimeOffset|DATE_FORMAT = '. fffffff zzz AAAA-MM-GG'|Oltre a anno, mese e giorno, sono inclusi 00 e 23 ore, da 00 a 59 minuti, da 00 a 59 secondi e 7 cifre per i millisecondi e la differenza di fuso orario che è stato inserito nel file di input come {+ &#124;-} HH:ss. Ad esempio, dopo l'ora senza legale Los Angeles risparmio è 8 ore rispetto all'ora UTC, il valore -08:00, nel file di input specifica il fuso orario per Los Angeles.|  
|DateTimeOffset|DATE_FORMAT = 'aaaa-MM-gg hh:mm:ss.ffffffftt zzz'|Oltre a anno, mese e giorno, sono inclusi 00-11 ore, da 00 a 59 minuti, da 00 a 59 secondi 7 cifre per i millisecondi, (AM, am, PM o pm) e la differenza di fuso orario. Vedere la descrizione della riga precedente.|  
|Time|DATE_FORMAT = 'Hh'|È presente alcun valore di data, solo 00 e 23 ore, da 00 a 59 minuti e da 00 a 59 secondi.|  
  
 Tutti i formati di data supportati:  
  
|datetime|smalldatetime|data|datetime2|datetimeoffset|  
|--------------|-------------------|----------|---------------|--------------------|  
|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fff]|[M [M]] M-[d] d-[Aa] aa hh: mm [: 00]|[M [M]] M-[d] d-[Aa] AA|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff]|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff] zzz|  
|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fff] [Aa]|[M [M]] M-[d] d-[Aa] aa hh: mm [: 00] [Aa]||[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff] [Aa]|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff] [Aa] zzz|  
|[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fff]|[M [M]] M-[Aa] AA-[d] d hh: mm [: 00]|[M [M]] M-[Aa] AA-[d] d|[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fffffff]|[M [M]] M-[Aa] AA-[d] d zzz hh.mm.ss [. fffffff]|  
|[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fff] [Aa]|[M [M]] M-[Aa] AA-[d] d hh: mm [: 00] [Aa]||[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fffffff] [Aa]|[M [M]] M-[Aa] AA-[d] [. fffffff] [Aa] hh: mm: d zzz|  
|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fff]|[Aa] AA-[[M] M] M-[d] d hh: mm [: 00]|[Aa] AA-[[M] M] M-[d] d|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fffffff]|[Aa] AA-[[M] M] M-[d] [. fffffff] hh: mm: d zzz|  
|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fff] [Aa]|[Aa] AA-[[M] M] M-[d] d hh: mm [: 00] [Aa]||[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fffffff] [Aa]|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fffffff] [Aa] zzz|  
|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fff]|[Aa] AA-[d] d-[[M] M] M hh: mm [: 00]|[Aa] AA - d [d]-[[M] M] M|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff]|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff] zzz|  
|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fff] [Aa]|[Aa] AA-[d] d-[[M] M] M hh: mm [: 00] [Aa]||[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff] [Aa]|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff] [Aa] zzz|  
|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fff]|[d] d-[[M] M] M-[Aa] aa hh: mm [: 00]|[d] d-[[M] M] M-[Aa] AA|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff]|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff] zzz|  
|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fff] [Aa]|[d] d-[[M] M] M-[Aa] aa hh: mm [: 00] [Aa]||[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff] [Aa]|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff] [Aa] zzz|  
|d [d]-[Aa] AA-[[M] M] M hh.mm.ss [. fff]|d [d]-[Aa] AA-[[M] M] M hh: mm [: 00]|d [d]-[Aa] AA-[[M] M] M|d [d]-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff]|[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff] zzz|  
|[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fff] [Aa]|[d] d-[Aa] AA-[[M] M] M hh: mm [: 00] [Aa]||[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff] [Aa]|[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff] [Aa] zzz|  
  
 Dettagli:  
  
-   Per separare i valori di mese, giorno e anno, è possibile utilizzare '-', '/' o '. '. Per semplicità, la tabella utilizza solo il separatore ':'.  
  
-   Per specificare il mese come testo utilizzare tre o più caratteri. Verranno interpretati come un numero di mesi con caratteri di 1 o 2.  
  
-   Per separare i valori di ora, utilizzare i ': ' simbolo.  
  
-   Lettere racchiuso tra parentesi quadre sono facoltative.  
  
-   Designare le lettere "tt" [AM | PM | am | pm]. AM è l'impostazione predefinita. Se si specifica "tt", il valore dell'ora (hh) deve essere compreso nell'intervallo da 0 a 12.  
  
-   Le lettere 'zzz' designare l'offset del fuso orario per fuso orario corrente del sistema nel formato {+ |-} HH:ss].  
  
 USE_TYPE_DEFAULT = {TRUE | **FALSE** }  
 Specifica come gestire valori mancanti nei file di testo delimitati quando PolyBase recupera i dati dal file di testo.  
  
 TRUE  
 Quando si recuperano dati dal file di testo, archiviare ogni valore mancante utilizzando il valore predefinito per il tipo di dati della colonna corrispondente nella definizione della tabella esterna. Ad esempio, sostituire un valore mancante con:  
  
-   0 se la colonna viene definita come una colonna numerica.  
  
-   Una stringa vuota "" se la colonna è una colonna stringa.  
  
-   1900-01-01 se la colonna è una colonna di date.  
  
 FALSE  
 Archiviare tutti i valori mancanti come NULL. Verranno importati tutti i valori NULL vengono archiviati utilizzando la parola NULL nel file di testo delimitato da virgole come la stringa 'NULL'.  
  
   Codifica = {'UTF8' | 'UTF16'}   
 In Azure SQL Data Warehouse PolyBase può leggere UTF8 e UTF16-LE con codificata di file di testo delimitati. In SQL Server e PDW, PolyBase non supporta la lettura UTF16 file codificato.
  
 DATA_COMPRESSION = *data_compression_method*  
 Specifica il metodo di compressione dati per i dati esterni. Quando DATA_COMPRESSION non è specificato, il valore predefinito è dati non compressi.  
 Per il corretto funzionamento, i file compressi Gzip devono avere l'estensione del file ".gz".
 
 Il tipo di formato DELIMITEDTEXT supporta i metodi di compressione:  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.GzipCodec'  

 Il tipo di formato RCFILE supporta questo metodo di compressione:  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
 Il tipo di formato file ORC supporta i metodi di compressione:  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.SnappyCodec'  
  
 Il tipo di formato di file PARQUET supporta i metodi di compressione:  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.GzipCodec'  
  
-   La compressione dei dati = 'org.apache.hadoop.io.compress.SnappyCodec'  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY EXTERNAL FILE FORMAT.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Il formato di file esterno è con ambito database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. È con ambito server in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Le opzioni di formato sono facoltative e si applicano solo ai file di testo delimitato da virgole.  
  
 Quando i dati vengono archiviati in un formato compresso, PolyBase verrà innanzitutto decomprimere i dati prima di restituire i record di dati.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni   
  
 Il delimitatore di riga nel file di testo delimitati deve essere supportato da LineRecordReader Hadoop, ovvero deve essere '\r', '\n' o '\r\n'. Non sono configurabili dall'utente.  
  
 Le combinazioni di metodi SerDe supportati con RCFiles, nonché i metodi di compressione di dati supportati sono elencati in precedenza in questo articolo. Non tutte le combinazioni supportate.  
  
 Il numero massimo di query di PolyBase simultanee è 32. Quando si eseguono query simultanee 32, ogni query può leggere un numero massimo di 33,000 file dal percorso di file esterno. La cartella radice e ogni sottocartella anche considerato come un file. Se il livello di concorrenza è minore di 32, il percorso del file esterno può contenere più di 33,000 file.  
  
 A causa dei limiti sul numero di file nella tabella esterna, è consigliabile archiviare i file inferiore a 30.000 principali e le sottocartelle della posizione del file esterno. Inoltre, si consiglia di mantenere il numero delle sottocartelle della cartella principale per un numero ridotto. Quando vengono fatto riferimento troppi file potrebbe verificarsi un'eccezione di memoria macchina virtuale Java.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco condiviso per l'oggetto formato di FILE esterno.  
  
## <a name="performance"></a>Prestazioni  
 Utilizzare sempre i file compressi, viene fornito con il compromesso tra il trasferimento di minore quantità di dati e migliorano l'utilizzo della CPU per comprimere e decomprimere i dati tra l'origine dati esterna e SQL Server.  
  
 File di testo compresso gzip non sono divisibili. Per migliorare le prestazioni per il file di testo compresso Gzip, si consiglia la generazione di più file archiviati nella stessa directory all'interno dell'origine dati esterna. Ciò consente a PolyBase per leggere e decomprimere i dati più veloce usando più processi di lettura e la decompressione. Il numero ideale di file compressi è il numero massimo di processi di lettore di dati per ogni nodo di calcolo. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], il numero massimo di processi di lettore dati è 8 per ogni nodo nella versione corrente. In [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], il numero massimo di processi di lettore di dati per ogni nodo varia in base al SLO. Vedere [Azure SQL Data Warehouse durante il caricamento di modelli e le strategie](https://blogs.msdn.microsoft.com/sqlcat/2016/02/06/azure-sql-data-warehouse-loading-patterns-and-strategies/) per informazioni dettagliate.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-create-a-delimitedtext-external-file-format"></a>A. Creare un formato di file esterno DELIMITEDTEXT  
 Questo esempio viene creato un formato di file esterno denominato *textdelimited1* per un file delimitato da testo. Il FORMAT_OPTIONS specificare i campi nel file saranno separati con un carattere barra verticale ' |'. Il file di testo viene anche compresso con Gzip codec. Se DATA_COMPRESSION non è specificato, il file di testo non compresso.  
  
 Per un file di testo delimitato, il metodo di compressione dei dati può essere il valore predefinito Codec, 'org.apache.hadoop.io.compress.DefaultCodec' o il Gzip Codec, 'org.apache.hadoop.io.compress.GzipCodec'.  
  
```  
CREATE EXTERNAL FILE FORMAT textdelimited1  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,  
    FORMAT_OPTIONS (  
        FIELD_TERMINATOR = '|',  
        DATE_FORMAT = 'MM/dd/yyyy' ),  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.GzipCodec'  
);  
```  
  
### <a name="b-create-an-rcfile-external-file-format"></a>B. Creare un formato di file esterno RCFile  
 Questo esempio viene creato un formato di file esterno per un RCFile che utilizza il org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe di metodo di serializzazione/deserializzazione. Specifica inoltre per utilizzare il Codec predefinito per il metodo di compressione dati. Se DATA_COMPRESSION non è specificato, il valore predefinito non è alcuna compressione.  
  
```  
CREATE EXTERNAL FILE FORMAT rcfile1  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe',  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec'  
);  
```  
  
### <a name="c-create-an-orc-external-file-format"></a>C. Creare un formato di file esterno ORC  
 Questo esempio viene creato un formato di file esterno per un file ORC che comprime i dati con il metodo di compressione dati org.apache.io.compress.SnappyCodec. Se DATA_COMPRESSION non è specificato, il valore predefinito non è alcuna compressione.  
  
```  
CREATE EXTERNAL FILE FORMAT orcfile1  
WITH (  
    FORMAT_TYPE = ORC,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
### <a name="d-create-a-parquet-external-file-format"></a>D. Creare un formato di file esterno PARQUET  
 Questo esempio viene creato un formato di file esterno per un file Parquet che comprime i dati con il metodo di compressione dati org.apache.io.compress.SnappyCodec. Se DATA_COMPRESSION non è specificato, il valore predefinito non è alcuna compressione.  
  
```  
CREATE EXTERNAL FILE FORMAT parquetfile1  
WITH (  
    FORMAT_TYPE = PARQUET,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT &#40; Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)  
  
  

