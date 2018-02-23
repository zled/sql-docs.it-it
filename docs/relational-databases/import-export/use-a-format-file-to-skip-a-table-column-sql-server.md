---
title: Usare un file di formato per ignorare una colonna di una tabella (SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 02/13/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: import-export
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8908c590ff97f09259635a407d1e37fc22956f20
ms.sourcegitcommit: aebbfe029badadfd18c46d5cd6456ea861a4e86d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a>Utilizzo di un file di formato per ignorare una colonna di una tabella (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Questo articolo descrive come usare un file di formato per evitare di importare la colonna di una tabella quando il campo non esiste nel file di dati di origine. Un file di dati può contenere un numero di campi inferiore rispetto al numero di colonne nella tabella di destinazione, ovvero è possibile ignorare l'importazione di una colonna, solo se viene soddisfatta almeno una delle due condizioni seguenti:
-   La colonna ignorata ammette i valori Null.
-   La colonna ignorata ha un valore predefinito.  
  
## <a name="sample-table-and-data-file"></a>Tabella e file di dati di esempio  
 Gli esempi in questo articolo prevedono una tabella denominata `myTestSkipCol` nello schema **dbo**. È possibile creare questa tabella in un database di esempio, ad esempio *WideWorldImporters* o *AdventureWorks*, o in qualsiasi altro database. Per creare la tabella, utilizzare il codice seguente:  
  
```sql
USE WideWorldImporters;  
GO  
CREATE TABLE myTestSkipCol   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) NULL,  
   Col3 nvarchar(50) not NULL  
   );  
GO  
```  
  
Gli esempi in questo articolo usano anche un file di dati di esempio, `myTestSkipCol2.dat`. Questo file di dati contiene solo due campi sebbene la tabella di destinazione contenga tre colonne.

```  
1,DataForColumn3  
1,DataForColumn3  
1,DataForColumn3  
```  
  
Per eseguire l'importazione in blocco dei dati da `myTestSkipCol2.dat` nella tabella `myTestSkipCol`, è necessario che il file di formato esegua il mapping del primo campo di dati a `Col1` e del secondo campo a `Col3`, ignorando `Col2`.  
  
## <a name="option-1---use-a-non-xml-format-file"></a>Opzione 1 - Usare un file di formato non XML  
È possibile usare un file di formato non XML per ignorare una colonna di tabella. Eseguire due passaggi:

1.   Usare l'utilità della riga di comando **bcp** per creare un file di formato non XML predefinito.

2.   Modificare il file di formato predefinito in un editor di testo.

Il file di formato modificato deve eseguire il mapping di ogni campo esistente alla colonna corrispondente nella tabella di destinazione. IL file deve indicare anche la colonna o le colonne della tabella da ignorare. 
  
### <a name="step-1---create-a-default-non-xml-format-file"></a>Passaggio 1 - Creare un file di formato non XML predefinito  
Creare un file di formato non XML predefinito per la tabella di esempio `myTestSkipCol` usando il comando **bcp** seguente al prompt dei comandi:  
  
```cmd
bcp WideWorldImporters..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T  
```  
  
Il comando precedente crea un file di formato non XML, `myTestSkipCol_Default.fmt`. Questo file di formato è chiamato *file di formato predefinito* perché è generato da **bcp**. Un file di formato predefinito descrive una corrispondenza uno-a-uno tra i campi del file di dati e le colonne di tabella.  
  
> [!IMPORTANT]  
>  Potrebbe essere necessario specificare il nome dell'istanza del server a cui ci si connette usando l'argomento `-S`. Potrebbe anche essere necessario specificare il nome utente e la password con gli argomenti `-U` e `-P`. Per altre informazioni, vedere [bcp Utility](../../tools/bcp-utility.md).  
  
 La figura seguente illustra i valori nei file di formato predefiniti di esempio. 
  
 ![file di formato non XML predefinito per myTestSkipCol](../../relational-databases/import-export/media/mytestskipcol-f-c-default-fmt.gif "file di formato non XML predefinito per myTestSkipCol")  
  
> [!NOTE]  
>  Per altre informazioni sui campi dei file di formato, vedere [File in formato non XML &#40;SQL Server&#41;](../../relational-databases/import-export/non-xml-format-files-sql-server.md).  
  
### <a name="step-2---modify-a-non-xml-format-file"></a>Passaggio 2 - Modificare un file di formato non XML  
Esistono due alternative per la modifica di un file di dati non XML predefinito. Entrambe consentono di indicare che il campo dati non esiste nel file di dati e che non devono essere inseriti dati nella colonna della tabella corrispondente.

Per ignorare una colonna di tabella, modificare il file di formato non XML predefinito, utilizzando una delle modalità alternative seguenti:  

#### <a name="option-1---remove-the-row"></a>Opzione 1 - Rimuovere la riga
Il metodo preferito per ignorare una colonna prevede tre passaggi principali.

1.   Eliminare innanzitutto eventuali righe del file di formato che descrivono un campo non presente nel file di dati di origine.
2.   Ridurre quindi il valore "Ordine dei campi nel file host" di ogni riga del file di formato che segue una riga eliminata. L'obiettivo sono i valori sequenziali "Ordine dei campi nel file host", da 1 a *n*, che riflettono l'effettiva posizione di ogni campo nel file di dati.
3.   Ridurre infine il valore nel campo "Numero di colonne" in modo da riflettere il numero effettivo di campi nel file di dati.  
  
L'esempio seguente si basa sul file di formato predefinito per la tabella `myTestSkipCol`, creato nel passaggio precedente "Creare un file di formato non XML predefinito" di questo argomento. Questo file di formato modificato esegue il mapping tra il primo campo dati e `Col1`, ignora `Col2`ed esegue il mapping tra il secondo campo dati e `Col3`. La riga per `Col2` è stata eliminata. Anche il delimitatore dopo il primo campo è stato modificato da `\t` a `,`.
  
```  
14.0  
2  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS  
```  
  
#### <a name="option-2---modify-the-row-definition"></a>Opzione 2 - Modificare la definizione di riga

In alternativa, per ignorare una colonna di tabella, è possibile modificare la definizione della riga del file di formato che corrisponde alla colonna di tabella. In questa riga del file di formato, i valori "lunghezza del prefisso," "lunghezza dei dati del file host" e "ordine delle colonne nel server" devono essere impostati su 0. Inoltre, i campi "terminatore" e "regole di confronto a livello di colonna" devono essere impostati su "" (NULL).  
  
Il valore "nome colonna server" richiede una stringa non vuota, sebbene il nome di colonna effettivo non sia necessario. Per i campi di formato restanti sono necessari i relativi valori predefiniti.  
  
L'esempio seguente deriva inoltre dal file di formato predefinito per la tabella `myTestSkipCol` .  
  
```  
14.0  
3  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       0       ""       0     Col2         ""  
3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS  
```  
  
### <a name="examples-with-a-non-xml-format-file"></a>Esempi con un file di formato non XML 
Anche gli esempi seguenti sono basati sulla tabella di esempio `myTestSkipCol` e sul file di dati di esempio `myTestSkipCol2.dat` precedentemente descritti in questo articolo.  
  
#### <a name="using-bulk-insert"></a>Utilizzo di BULK INSERT  
Questo esempio funziona usando uno dei file di formato non XML modificati creati come descritto nella sezione precedente. In questo esempio, il file di formato modificato è denominato `myTestSkipCol2.fmt`. Per usare `BULK INSERT` per importare in blocco il file di dati `myTestSkipCol2.dat`, in SSMS, eseguire il codice seguente. Aggiornare i percorsi di file system per il percorso dei file di esempio nel computer in uso.
  
```sql  
USE WideWorldImporters;  
GO  
BULK INSERT myTestSkipCol   
   FROM 'C:\myTestSkipCol2.dat'   
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');  
GO  
SELECT * FROM myTestSkipCol;  
GO  
```  
  
## <a name="option-2---use-an-xml-format-file"></a>Opzione 2 - Usare un file di formato XML  

-   Con `bcp` e `BULK INSERT`. Con un file di formato XML non è possibile ignorare una colonna quando si sta eseguendo l'importazione diretta in una tabella usando un comando **bcp** o un'istruzione `BULK INSERT`. È tuttavia possibile importare un'intera tabella a eccezione dell'ultima colonna. Se si desidera ignorare una colonna diversa dall'ultima, è necessario creare una vista della tabella di destinazione che contiene solo le colonne contenute nel file di dati. In seguito sarà possibile eseguire un'importazione bulk dei dati da tale file nella vista.  
  
-   Con `OPENROWSET(BULK...)` Per usare un file di formato XML per ignorare una colonna di tabella usando `OPENROWSET(BULK...)`, è necessario specificare un elenco esplicito di colonne nell'elenco di selezione e anche nella tabella di destinazione, come illustrato di seguito:  
  
    ```sql
    INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...) 
    ```
  
### <a name="step-1---create-a-default-non-xml-format-file"></a>Passaggio 1 - Creare un file di formato non XML predefinito   

Questi esempi di file di formato XML modificati sono basati sulla tabella `myTestSkipCol` e sul file di dati di esempio precedentemente creati nella sezione "Tabella e file di dati di esempio" in questo argomento.

Il comando **bcp** seguente crea un file di formato XML predefinito per la tabella `myTestSkipCol` :  
  
```cmd
bcp WideWorldImporters..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T  
```  
  
Il file di formato non XML predefinito risultante descrive una corrispondenza uno-a-uno tra i campi del file di dati e le colonne di tabella, come segue:  
  
```xml
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Per informazioni sulla struttura dei file di formato XML, vedere [File in formato XML &#40;SQL Server&#41;](../../relational-databases/import-export/xml-format-files-sql-server.md).  

### <a name="step-2---modify-an-xml-format-file"></a>Passaggio 2 - Modificare un file di formato XML

Di seguito è riportato il file di formato XML modificato `myTestSkipCol2.xml` che ignora `Col2`. Le voci `FIELD` e `ROW` per `Col2` sono state rimosse e le altre voci sono state rinumerate. Anche il delimitatore dopo il primo campo è stato modificato da `\t` a `,`.

```xml
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
 
### <a name="examples-with-an-xml-format-file"></a>Esempi con un file di formato XML   
Gli esempi in questa sezione usano la tabella di esempio `myTestSkipCol` e il file di dati di esempio `myTestSkipCol2.dat` precedentemente creati nella sezione "Tabella e file di dati di esempio" in questo argomento. Per importare i dati da `myTestSkipCol2.dat` nella tabella `myTestSkipCol` , gli esempi utilizzano il file di formato XML modificato seguente, `myTestSkipCol2.xml`,   
  
#### <a name="using-openrowsetbulk"></a>Utilizzo di OPENROWSET(BULK...)  
Nell'esempio seguente viene utilizzato il provider di set di righe con lettura bulk `OPENROWSET` e il file di formato `myTestSkipCol2.xml` . Nell'esempio viene eseguita l'importazione bulk del file di dati `myTestSkipCol2.dat` nella tabella `myTestSkipCol` . L'istruzione contiene un elenco esplicito di colonne nell'elenco selezionato e nella tabella di destinazione, come richiesto.  
  
In SSMS eseguire il codice seguente. Aggiornare i percorsi di file system per il percorso dei file di esempio nel computer in uso.
  
```sql  
USE WideWorldImporters;  
GO  
INSERT INTO myTestSkipCol  
  (Col1,Col3)  
    SELECT Col1,Col3  
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',  
      FORMATFILE='C:\myTestSkipCol2.Xml'    
       ) as t1 ;  
GO  
```  
  
#### <a name="using-bulk-import-with-a-view"></a>Uso di BULK IMPORT con una visualizzazione  
L'esempio seguente crea la visualizzazione `v_myTestSkipCol` nella tabella `myTestSkipCol`. Questa vista ignora la seconda colonna della tabella, `Col2`. Nell'esempio viene quindi utilizzato `BULK INSERT` per importare il file di dati `myTestSkipCol2.dat` in questa vista.  
  
In SSMS eseguire il codice seguente. Aggiornare i percorsi di file system per il percorso dei file di esempio nel computer in uso. 
  
```sql  
USE WideWorldImporters;  
GO  

CREATE VIEW v_myTestSkipCol AS  
    SELECT Col1,Col3  
    FROM myTestSkipCol;  
GO  
  
BULK INSERT v_myTestSkipCol  
FROM 'C:\myTestSkipCol2.dat'  
WITH (FORMATFILE='C:\myTestSkipCol2.xml');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Utilizzo di un file di formato per ignorare una colonna di una tabella &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)   
 [Utilizzo di un file di formato per eseguire il mapping tra le colonne della tabella e i campi del file di dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)   
 [Utilizzo di un file di formato per l'importazione bulk dei dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
  
