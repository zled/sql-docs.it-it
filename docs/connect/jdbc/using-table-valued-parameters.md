---
title: Utilizzo di parametri con valori di tabella | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 356e81dc6faf25e12c4edd51d1927ac53c5b3a38
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-table-valued-parameters"></a>Utilizzo di parametri con valori di tabella
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Parametri con valori di tabella forniscono un modo semplice per effettuare il marshalling di più righe di dati da un'applicazione client a SQL Server senza richiedere più round trip o logica speciale sul lato di server per l'elaborazione dei dati. È possibile utilizzare parametri con valori di tabella per incapsulare le righe di dati in un'applicazione client e inviare i dati al server in un singolo comando con parametri. Le righe di dati in ingresso vengono archiviate in una variabile di tabella che può quindi essere utilizzata tramite Transact-SQL.  
  
 I valori di colonna nei parametri con valori di tabella è possibile accedere tramite istruzioni Transact-SQL SELECT standard. I parametri con valori di tabella sono fortemente tipizzati e la loro struttura viene convalidata automaticamente. Le dimensioni dei parametri con valori di tabella sono limitata solo dalla memoria del server.  
  
> [!NOTE]  
>  Supporto per i parametri con valori di tabella è disponibile a partire da Microsoft JDBC Driver 6.0 per SQL Server.  
  
> [!NOTE]  
>  È possibile restituire dati in un parametro con valori di tabella. I parametri con valori di tabella sono di solo input. la parola chiave OUTPUT non è supportata.  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere le risorse seguenti.  
  
|Risorsa|Description|  
|--------------|-----------------|  
|[Parametri con valori di tabella (motore di Database)](http://go.microsoft.com/fwlink/?LinkId=98363) nella documentazione Online di SQL Server|Viene descritto come creare e utilizzare i parametri con valori di tabella|  
|[Tipi di tabella definiti dall'utente](http://go.microsoft.com/fwlink/?LinkId=98364) nella documentazione Online di SQL Server|Vengono descritti i tipi di tabella definito dall'utente vengono utilizzati per dichiarare i parametri con valori di tabella|  
|Il [motore di Database di Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=120507) sezione di CodePlex|Sono inclusi esempi che illustrano come utilizzare la funzionalità e le funzionalità di SQL Server|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passare più righe nelle versioni precedenti di SQL Server  
 Prima di parametri con valori di tabella sono stati introdotti in SQL Server 2008, le opzioni per passare più righe di dati a una stored procedure o un comando SQL con parametri erano limitate. Uno sviluppatore può scegliere tra le opzioni seguenti per passare più righe al server:  
  
-   Utilizzare una serie di parametri singoli per rappresentare i valori in più colonne e righe di dati. La quantità di dati che possono essere passati tramite questo metodo è limitata dal numero di parametri consentiti. Procedure di SQL Server possono avere al massimo 2100 parametri. Logica sul lato server è necessaria per assemblare questi singoli valori in una variabile di tabella o una tabella temporanea per l'elaborazione.  
  
-   Aggregare più valori di dati in stringhe delimitate o documenti XML e quindi passare tali valori di testo a una routine o istruzione. Questo richiede la procedura o l'istruzione includa la logica necessaria per la convalida di strutture di dati e la separazione di valori.  
  
-   Creare una serie di istruzioni SQL singole per modifiche ai dati che interessano più righe. Le modifiche possono essere inviate al server individualmente o raggruppate. Tuttavia, anche quando l'invio in batch contenenti più istruzioni, ogni istruzione viene eseguita separatamente nel server.  
  
-   Utilizzare il programma di utilità bcp o [SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) oggetto per caricare numerose righe di dati in una tabella. Sebbene questa tecnica è molto efficiente, non supporta l'elaborazione sul lato server, a meno che i dati vengono caricati in una tabella temporanea o variabile di tabella.  
  
## <a name="creating-table-valued-parameter-types"></a>Creazione di tipi di parametro con valori di tabella  
 Parametri con valori di tabella si basano sulle strutture di tabella fortemente tipizzate definite tramite istruzioni Transact-SQL CREATE TYPE. È necessario creare un tipo di tabella e definire la struttura in SQL Server prima di poter utilizzare i parametri con valori di tabella nelle applicazioni client. Per ulteriori informazioni sulla creazione di tipi di tabella, vedere [tipi di tabella definiti dall'utente](http://go.microsoft.com/fwlink/?LinkID=98364) nella documentazione Online di SQL Server.  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Dopo aver creato un tipo di tabella, è possibile dichiarare i parametri con valori di tabella basati su tale tipo. Nel frammento Transact-SQL seguente viene illustrato come dichiarare un parametro con valori di tabella in una definizione di stored procedure. Si noti che la parola chiave READONLY è necessaria dichiarare un parametro con valori di tabella.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modifica di dati con parametri con valori di tabella (Transact-SQL)  
 Parametri con valori di tabella possono essere utilizzati nelle modifiche dei dati basata su set che interessano più righe tramite l'esecuzione di una singola istruzione. Ad esempio, è possibile selezionare tutte le righe in un parametro con valori di tabella e inserirli in una tabella di database oppure è possibile creare un'istruzione update creando un join di un parametro con valori di tabella per la tabella che si desidera aggiornare.  
  
 L'istruzione UPDATE di Transact-SQL seguente viene illustrato come utilizzare un parametro con valori di tabella creando un join alla tabella Categories. Quando si utilizza un parametro con valori di tabella con un JOIN in una clausola FROM, è necessario anche alias, come illustrato di seguito, dove il parametro con valori di tabella viene usato l'alias "ec":  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 In questo esempio di Transact-SQL viene illustrato come selezionare le righe da un parametro con valori di tabella per eseguire un inserimento in una singola operazione basata su set.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Limitazioni di parametri con valori di tabella  
 Sono previste alcune limitazioni per i parametri con valori di tabella:  
  
-   È possibile passare parametri con valori di tabella di funzioni definite dall'utente.  
  
-   I parametri con valori di tabella possono essere indicizzati solo per supportare vincoli UNIQUE o PRIMARY KEY. SQL Server non vengono gestite statistiche sui parametri con valori di tabella.  
  
-   I parametri con valori di tabella sono di sola lettura nel codice Transact-SQL. Non è possibile aggiornare i valori di colonna nelle righe di un parametro con valori di tabella e non è possibile inserire o eliminare righe. Per modificare i dati che viene passati a una stored procedure o istruzione con parametri in parametri con valori di tabella, è necessario inserire i dati in una tabella temporanea o in una variabile di tabella.  
  
-   È possibile utilizzare istruzioni ALTER TABLE per modificare la struttura di parametri con valori di tabella.
-   È possibile trasmettere oggetti di grandi dimensioni in un parametro con valori di tabella.  
  
## <a name="configuring-a-table-valued-parameter"></a>Configurazione di un parametro con valori di tabella  
 A partire da Microsoft JDBC Driver 6.0 per SQL Server, sono supportati i parametri con valori di tabella con un'istruzione con parametri o una stored procedure con parametri. I parametri con valori di tabella possono essere compilati da un SQLServerDataTable, da un set di risultati o da un utente purché l'implementazione dell'interfaccia ISQLServerDataRecord. Quando si imposta un parametro con valori di tabella per una query preparata, è necessario specificare un nome di tipo che deve corrispondere al nome di un tipo compatibile creato in precedenza nel server.  
  
 I frammenti di codice seguente viene illustrato come configurare un parametro con valori di tabella con un SQLServerPreparedStatement e con un SQLServerCallableStatement per inserire i dati. Qui sourceTVPObject può essere un SQLServerDataTable, o un set di risultati o un oggetto ISQLServerDataRecord. Gli esempi presuppongono la connessione è un oggetto connessione attivo.  
  
```  
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =   
    (SQLServerPreparedStatement) connection.prepareStatement(“INSERT INTO dbo.Categories SELECT * FROM ?”);  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```  
  
```  
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =   
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");       
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```  
  
> [!NOTE]  
>  Nella sezione **API di parametro con valori di tabella per il Driver JDBC** sotto per un elenco completo delle API disponibili per l'impostazione del parametro con valori di tabella.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Passando un parametro con valori di tabella come oggetto SQLServerDataTable  
 A partire da Microsoft JDBC Driver 6.0 per SQL Server, la classe SQLServerDataTable rappresenta una tabella in memoria dei dati relazionali. In questo esempio viene illustrato come costruire un parametro con valori di tabella dai dati in memoria usando l'oggetto SQLServerDataTable. Il codice prima crea un oggetto SQLServerDataTable, definisce lo schema e popola la tabella con dati. Nel codice viene quindi configurato un SQLServerPreparedStatement che passa a questa tabella di dati come parametro con valori di tabella a SQL Server.  
  
```  
// Assumes connection is an active Connection object.  
  
// Create an in-memory data table.  
SQLServerDataTable sourceDataTable = new SQLServerDataTable();   
  
// Define metadata for the data table.  
sourceDataTable.addColumnMetadata("CategoryID" ,java.sql.Types.INTEGER);   
sourceDataTable.addColumnMetadata("CategoryName" ,java.sql.Types.NVARCHAR);   
  
// Populate the data table.  
sourceDataTable.addRow(1, "CategoryNameValue1");   
sourceDataTable.addRow(2, "CategoryNameValue2");   
  
// Pass the data table as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =   
        (SQLServerPreparedStatement) connection.prepareStatement(  
            "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceDataTable);  
pStmt.execute();  
```  
  
> [!NOTE]  
>  Nella sezione **API di parametro con valori di tabella per il Driver JDBC** sotto per un elenco completo delle API disponibili per l'impostazione del parametro con valori di tabella.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Passando un parametro con valori di tabella come un oggetto ResultSet  
 In questo esempio viene illustrato come eseguire il flusso di righe di dati da un set di risultati a un parametro con valori di tabella. Il codice recupera i dati da una tabella di origine in un crea un oggetto SQLServerDataTable, definisce lo schema e popola la tabella con dati. Nel codice viene quindi configurato un SQLServerPreparedStatement che passa a questa tabella di dati come parametro con valori di tabella a SQL Server.  
  
```  
// Assumes connection is an active Connection object.  
  
// Create the source ResultSet object. Here SourceCategories is a table defined with the same schema as Categories table.   
ResultSet sourceResultSet = connection.createStatement().executeQuery("SELECT * FROM SourceCategories");  
  
// Pass the source result set as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =   
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceResultSet);  
pStmt.execute();  
```  
  
> [!NOTE]  
>  Nella sezione **API di parametro con valori di tabella per il Driver JDBC** sotto per un elenco completo delle API disponibili per l'impostazione del parametro con valori di tabella.  
  
## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Passando un parametro con valori di tabella come oggetto ISQLServerDataRecord  
 A partire da Microsoft JDBC Driver 6.0 per SQL Server, una nuova interfaccia ISQLServerDataRecord è disponibile per il flusso di dati (a seconda di come l'utente fornisce l'implementazione per tale) utilizzando un parametro con valori di tabella. Nell'esempio seguente viene illustrato come implementare l'interfaccia ISQLServerDataRecord e come passare come parametro con valori di tabella. Per semplicità, nell'esempio seguente passa una sola riga con valori hardcoded per il parametro con valori di tabella. Idealmente, l'utente potrebbe implementare questa interfaccia per trasmettere flussi di righe da qualsiasi origine, ad esempio file di testo.  
  
```  
class MyRecords implements ISQLServerDataRecord  
{  
    int currentRow = 0;  
    Object[] row = new Object[2];  
  
    MyRecords(){  
        // Constructor. This implementation has just one row.   
        row[0] = new Integer(1);  
        row[1] = "categoryName1";  
    }  
  
    public int getColumnCount(){  
        // Return the total number of columns, for this example it is 2.  
        return 2;  
    }  
  
    public SQLServerMetaData getColumnMetaData(int columnIndex) {  
        // Return the column metadata.  
        if (1 == columnIndex)  
            return new SQLServerMetaData("CategoryID", java.sql.Types.INTEGER);  
        else  
            return new SQLServerMetaData("CategoryName", java.sql.Types.NVARCHAR);  
    }  
  
    public Object[] getRowData(){  
        // Return the columns in the current row as an array of objects. This implementation has just one row.  
        return row;       
    }  
  
    public boolean next(){  
        // Move to the next row. This implementation has just one row, after processing the first row, return false.  
        currentRow++;  
        if (1 == currentRow)  
            return true;  
        else  
            return false;  
    }     
}  
  
// Following code demonstrates how to pass MyRecords object as a table-valued parameter.  
MyRecords sourceRecords = new MyRecords();  
SQLServerPreparedStatement pStmt =   
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceRecords);  
pStmt.execute();  
```  
  
> [!NOTE]  
>  Nella sezione **API di parametro con valori di tabella per il Driver JDBC** sotto per un elenco completo delle API disponibili per l'impostazione del parametro con valori di tabella.  
    
## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Parametro con valori di tabella API per il Driver JDBC  
 **SQLServerMetaData**  
  
 Questa classe rappresenta i metadati per una colonna. Utilizzato nell'interfaccia ISQLServerDataRecord per passare i metadati della colonna per il parametro con valori di tabella. I metodi in questa classe sono:  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica SQLServerMetaData (stringa columnName sqlType int, int mobile e precisione, scala int, boolean useServerDefault, isUniqueKey booleano, sortOrder SQLServerSortOrder sortOrdinal int)|Inizializza una nuova istanza della SQLServerMetaData con il nome di colonna specificato, il tipo di sql, precisione, scala e il server predefinito. Questo form del costruttore supporta parametri con valori di tabella, consentendo di specificare se la colonna è univoca nel parametro con valori di tabella, l'ordinamento per la colonna e il numero ordinale della colonna di ordinamento. <br><br>useServerDefault - specifica se questa colonna deve utilizzare il valore predefinito del server; Valore predefinito è false.<br>isUniqueKey - indica se la colonna nel parametro con valori di tabella è univoca. Valore predefinito è false.<br>sortOrder - indica l'ordinamento per una colonna. Valore predefinito è SQLServerSortOrder.Unspecified.<br>sortOrdinal - specifica l'ordinale della colonna di ordinamento. sortOrdinal inizia da 0. Valore predefinito è -1.|
|pubblica SQLServerMetaData (stringa columnName, sqlType int)|Inizializza una nuova istanza della SQLServerMetaData utilizzando il nome della colonna e il tipo sql.|  
|pubblica SQLServerMetaData (stringa columnName, sqlType int, int precisione, scala int)|Inizializza una nuova istanza della SQLServerMetaData utilizzando il nome della colonna, tipo sql, precisione e scala.|  
|Pubblica SQLServerMetaData (SQLServerMetaData sqlServerMetaData)|Inizializza una nuova istanza del primo SQLServerMetaData un altro oggetto SQLServerMetaData.|  
|pubblica getColumName() stringa|Recupera il nome della colonna.|  
|pubblica int getSqlType()|Recupera il tipo di codice sql java.|  
|pubblica int getPrecision()|Recupera la precisione del tipo passato alla colonna.|  
|pubblica int getScale()|Recupera la scala del tipo passato alla colonna.|  
|pubblica SQLServerSortOrder getSortOrder()|Recupera il tipo di ordinamento.|
|pubblica int getSortOrdinal()|Recupera il numero ordinale di ordinamento.|
|pubblica isUniqueKey() booleano|Restituisce se la colonna è univoca.|
|pubblica useServerDefault() booleano|Restituisce se la colonna utilizza il valore predefinito del server.|
  
 **SQLServerSortOrder**
 
 Un'enumerazione che definisce l'ordinamento. I valori possibili sono crescente, decrescente e non specificato. 
  
 **SQLServerDataTable**  
  
 Questa classe rappresenta una tabella di dati in memoria da utilizzare con i parametri con valori di tabella. I metodi in questa classe sono:  
  
|Nome|Description|  
|----------|-----------------|  
|SQLServerDataTable() pubblica|Inizializza una nuova istanza della SQLServerDataTable.|  
|Iteratore pubblica < voce\<intero, Object [] >> getIterator()|Recupera un iteratore sulle righe della tabella di dati.|  
|pubblica addColumnMetadata void (stringa columnName, sqlType int)|Aggiunge i metadati per la colonna specificata.|  
|pubblica addColumnMetadata void (SQLServerDataColumn colonna)|Aggiunge i metadati per la colonna specificata.|  
|pubblica addRow void (valori dell'oggetto...)|Aggiunge una riga di dati alla tabella di dati.|  
|Mappa pubblica\<intero, SQLServerDataColumn > getColumnMetadata()|Recupera i metadati di colonna della tabella dati.|
|pubblica Clear (void) |Cancella questa tabella di dati. |  
  
 **SQLServerDataColumn**  
  
 Questa classe rappresenta una colonna della tabella di dati in memoria rappresentata da SQLServerDataTable. I metodi in questa classe sono:  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica SQLServerDataColumn (stringa columnName, sqlType int)|Inizializza una nuova istanza della SQLServerDataColumn con il nome della colonna e il tipo.|  
|pubblica getColumnName() stringa|Recupera il nome della colonna.|  
|pubblica int getColumnType()|Recupera il tipo di colonna.|  
  
 **ISQLServerDataRecord**  
  
 Questa classe rappresenta un'interfaccia che gli utenti possono implementare un flusso di dati a un parametro con valori di tabella. I metodi in questa interfaccia sono:  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica SQLServerMetaData getColumnMetaData (int colonna).|Recupera i metadati della colonna dell'indice della colonna specificata.|  
|pubblica int getColumnCount();|Recupera il numero totale di colonne.|  
|pubblica oggetto [] getRowData();|Recupera i dati per la riga corrente come una matrice di oggetti.|  
|pubblica booleano Next ();|Passa alla riga successiva. Restituisce True se il passaggio ha esito positivo ed è presente una riga successiva, false in caso contrario.|  
  
 **SQLServerPreparedStatement**  
  
 I metodi seguenti sono stati aggiunti a questa classe supporta il passaggio di parametri con valori di tabella.  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica setStructured void finale (parameterIndex int, String tvpName, SQLServerDataTable tvpDataTbale)|Popola un parametro con valori di tabella con una tabella dati. parameterIndex è l'indice del parametro, tvpName è il nome del parametro con valori di tabella e tvpDataTable è l'oggetto tabella di origine dati.|  
|pubblica setStructured void finale (parameterIndex int, String tvpName, tvpResultSet ResultSet)|Popola un parametro con valori di tabella con un set di risultati recuperato dalla tabella anther. parameterIndex è l'indice del parametro, tvpName è il nome del parametro con valori di tabella e tvpResultSet è l'oggetto set di risultati di origine.|  
|pubblica setStructured void finale (parameterIndex int, String tvpName, ISQLServerDataRecord tvpDataRecord)|Popola un parametro con valori di tabella con un oggetto ISQLServerDataRecord. ISQLServerDataRecord viene utilizzato per il flusso di dati e l'utente decide come utilizzarla. parameterIndex è l'indice del parametro, tvpName è il nome del parametro con valori di tabella e tvpDataRecord è un oggetto ISQLServerDataRecord.|  
  
 **SQLServerCallableStatement**  
  
 I metodi seguenti sono stati aggiunti a questa classe supporta il passaggio di parametri con valori di tabella.  
  
|Nome|Description|  
|----------|-----------------|  
|pubblica setStructured void finale (paratemeterName stringa, stringa tvpName, SQLServerDataTable tvpDataTable)|Popola un parametro con valori di tabella passato a una stored procedure con una tabella dati. paratemeterName è il nome del parametro, tvpName è il nome del tipo TVP e tvpDataTable è l'oggetto tabella di dati.|  
|pubblica setStructured void finale (paratemeterName stringa, stringa tvpName, tvpResultSet ResultSet)|Popola un parametro con valori di tabella passato a una stored procedure con un set di risultati recuperati da un'altra tabella. paratemeterName è il nome del parametro, tvpName è il nome del tipo TVP e tvpResultSet è l'oggetto set di risultati di origine.|  
|pubblica setStructured void finale (paratemeterName stringa, stringa tvpName, ISQLServerDataRecord tvpDataRecord)|Popola un parametro con valori di tabella passato a una stored procedure con un oggetto ISQLServerDataRecord. ISQLServerDataRecord viene utilizzato per il flusso di dati e l'utente decide come utilizzarla. paratemeterName è il nome del parametro, tvpName è il nome del tipo TVP e tvpDataRecord è un oggetto ISQLServerDataRecord.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
