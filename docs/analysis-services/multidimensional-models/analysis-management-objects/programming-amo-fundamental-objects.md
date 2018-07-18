---
title: Programmazione di oggetti fondamentali AMO | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7d1a41e3682023862c69cc74bf961f279f99689e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="programming-amo-fundamental-objects"></a>Programmazione di oggetti fondamentali AMO
  Gli oggetti fondamentali sono in genere oggetti di semplice utilizzo che solitamente vengono creati e di cui successivamente viene creata un'istanza. Quando non sono più necessari, l'utente si disconnette da tali oggetti. Le classi fondamentali includono gli oggetti <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource> e <xref:Microsoft.AnalysisServices.DataSourceView>. L'unico oggetto complesso tra gli oggetti fondamentali AMO è <xref:Microsoft.AnalysisServices.DataSourceView>, per cui è necessario utilizzare dettagli per la compilazione del modello astratto che rappresenta la vista origine dati.  
  
 Gli oggetti <xref:Microsoft.AnalysisServices.Server> e <xref:Microsoft.AnalysisServices.Database> sono in genere necessari per utilizzare gli oggetti contenuti, ad esempio gli oggetti OLAP o quelli di data mining.  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti server](#ServerObjects)  
  
-   [Oggetti eccezione AMOException](#AMO)  
  
-   [Oggetti di database](#DatabaseObjects)  
  
-   [Oggetti DataSource](#DataSource)  
  
-   [Oggetti DataSourceView](#DSV)  
  
##  <a name="ServerObjects"></a> Oggetti server  
 Per utilizzare un oggetto <xref:Microsoft.AnalysisServices.Server>, è necessario connettersi al server e verificare se l'oggetto <xref:Microsoft.AnalysisServices.Server> è connesso al server. In questo caso, è necessario disconnettere <xref:Microsoft.AnalysisServices.Server> dal server.  
  
### <a name="connecting-to-the-server-object"></a>Connessione all'oggetto Server  
 La connessione al server viene stabilita se si dispone della stringa di connessione corretta.  
  
 Il codice seguente esempio viene restituita una <xref:Microsoft.AnalysisServices.Server> oggetto se la connessione ha esito positivo o restituisce **null** se si verifica un errore. Durante il processo di connessione gli errori vengono gestiti in un costrutto try/catch. Gli errori AMO vengono rilevati tramite la classe di eccezione <xref:Microsoft.AnalysisServices.AmoException>. In questo esempio l'errore viene visualizzato in una finestra di messaggio.  
  
```  
static Server ServerConnect( String strStringConnection)  
{  
    string methodCaption = "ServerConnect method";  
    Server svr = new Server();  
    try  
    {  
        svr.Connect(strStringConnection);  
    }  
    #region ErrorHandling  
    catch (AmoException e)  
    {  
        MessageBox.Show( "AMO exception " + e.ToString());  
        svr = null;  
    }  
    catch (Exception e)  
    {  
        MessageBox.Show("General exception " + e.ToString());  
        svr = null;  
    }  
    #endregion  
  
    return svr;  
}  
```  
  
 Di seguito viene riportata la struttura della stringa di connessione:  
  
 "**Origine dati =**\<nome server >".  
  
 Per ulteriori informazioni sulla stringa di connessione, vedere <xref:Microsoft.SqlServer.Management.Common.OlapConnectionInfo.ConnectionString%2A>.  
  
### <a name="validating-the-connection"></a>Convalida della connessione  
 Prima di programmare gli oggetti <xref:Microsoft.AnalysisServices.Server>, è necessario verificare di essere ancora connessi al server. Nell'esempio di codice seguente viene illustrato come eseguire questa operazione. Nell'esempio si presuppone che `svr` sia un oggetto <xref:Microsoft.AnalysisServices.Server> che esiste nel codice.  
  
```  
if ( (svr != null) && ( svr.Connected))  
{  
    // Do what it is needed if connection is good  
}  
```  
  
### <a name="disconnecting-from-the-server"></a>Disconnessione dal server  
 Appena l'operazione è stata completata, è possibile disconnettersi dal server tramite il metodo Disconnect. Nell'esempio di codice seguente viene illustrato come eseguire questa operazione. Nell'esempio si presuppone che `svr` sia un oggetto <xref:Microsoft.AnalysisServices.Server> che esiste nel codice.  
  
```  
if ( (svr != null) && ( svr.Connected))  
{  
    svr.Disconnect()  
}  
```  
  
###  <a name="AMO"></a> Oggetti eccezione AmoException  
 In caso di rilevamento di problemi, in AMO verrà generata un'eccezione. Per una spiegazione dettagliata delle eccezioni, vedere [AMO altre classi e metodi](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md). Nel codice di esempio seguente viene illustrato il modo corretto per rilevare le eccezioni in AMO:  
  
```  
try  
{  
   //... some AMO code in here  
}  
  
catch (  OutOfSynchException e)  
{  
   // error handling code for OutOfSynchException   
}  
  
catch (  OperationException e)  
{  
   // error handling code for OperationException   
}   
  
catch (  ResponseFormatException e)  
  
{  
   // error handling code for ResponseFormatException   
}   
  
catch (  ConnectionException e)  
  
{  
   // error handling code for ConnectionException   
}  
  
catch (  AMOException e)  
  
{  
   //... here is the place where you end if it is an AMO exception, but none of the previous exceptions  
   // if you start with AMOException in the first catch you will never see any one of the previous exceptions  
}  
```  
  
##  <a name="DatabaseObjects"></a> Oggetti di database  
 L'utilizzo di un oggetto <xref:Microsoft.AnalysisServices.Database> è estremamente semplice poiché si ottiene un database esistente dalla raccolta di database dell'oggetto <xref:Microsoft.AnalysisServices.Server>.  
  
### <a name="creating-dropping-and-finding-a-database"></a>Creazione, eliminazione e individuazione di un database  
 Nell'esempio di codice seguente viene illustrato come creare un database tramite un nome di database. Prima di creare il database, eseguire una query sull'oggetto <xref:Microsoft.AnalysisServices.DatabaseCollection> del server per verificare se il database esiste. In questo caso il database viene eliminato e successivamente creato. In caso contrario il database viene creato. Se il database deve essere eliminato, viene innanzitutto acquisito dalla raccolta di database.  
  
```  
static Database CreateDatabase(Server svr, String DatabaseName)  
{  
    Database db = null;  
    if ( (svr != null) && ( svr.Connected))  
    {  
        // Drop the database if it already exists  
        db = svr.Databases.FindByName(DatabaseName);  
        if (db != null)  
        {  
            db.Drop();  
        }  
  
        // Create the database  
        db = svr.Databases.Add(DatabaseName);  
        db.Update();  
    }  
  
    return db;  
}  
```  
  
 Per determinare se un database esiste nella raccolta di database, viene utilizzato il metodo FindByName. Se il database esiste, il metodo restituisce l'oggetto di database trovato. In caso contrario, restituisce un oggetto Null.  
  
 Appena l'oggetto <xref:Microsoft.AnalysisServices.Database> è stato aggiunto alla raccolta di database, il server deve essere aggiornato tramite il metodo Update. Se non si aggiorna il server, l'oggetto <xref:Microsoft.AnalysisServices.Database> non verrà creato nel server.  
  
### <a name="processing-a-database"></a>Elaborazione di un database  
 L'elaborazione di un database e di tutti gli oggetti figlio è un'operazione estremamente semplice perché nell'oggetto <xref:Microsoft.AnalysisServices.Database> è incluso un metodo Process.  
  
 Sebbene non siano necessari, nel metodo Process possono essere inclusi parametri. Se viene specificato alcun parametro, quindi verranno elaborati tutti gli oggetti figlio con i relativi **ProcessDefault** opzione. Per ulteriori informazioni sulle opzioni di elaborazione, vedere <xref:Microsoft.AnalysisServices.Database>.  
  
1.  Nel codice di esempio seguente viene elaborato un database in base al relativo valore predefinito.  
  
```  
static Database ProcessDatabase(Database db, ProcessType pt)  
{  
    db.Process( pt);  
    return db;  
}  
```  
  
##  <a name="DataSource"></a> Oggetti DataSource  
 Un oggetto <xref:Microsoft.AnalysisServices.DataSource> costituisce il collegamento tra [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e il database in cui risiedono i dati. Lo schema che rappresenta il modello sottostante per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene definito dall'oggetto <xref:Microsoft.AnalysisServices.DataSourceView>. Un oggetto <xref:Microsoft.AnalysisServices.DataSource> può essere considerato una stringa di connessione al database in cui risiedono i dati.  
  
 Nell'esempio di codice seguente viene illustrato come creare un oggetto <xref:Microsoft.AnalysisServices.DataSource>. Nell'esempio viene eseguita la verifica dell'esistenza del server e del database e della presenza della connessione dell'oggetto <xref:Microsoft.AnalysisServices.Server>. Se l'oggetto <xref:Microsoft.AnalysisServices.DataSource> esiste, viene eliminato e creato nuovamente. L'oggetto <xref:Microsoft.AnalysisServices.DataSource> viene creato con lo stesso nome e ID interno. In questo esempio non viene eseguito alcun controllo sulla stringa di connessione per verificarla.  
  
```  
static string CreateDataSource(Database db, string strDataSourceName, string strConnectionString)  
{  
        Server svr = db.Parent;  
        DataSource ds = db.DataSources.FindByName(strDataSourceName);  
        if (ds != null)  
            ds.Drop();  
        // Create the data source  
        ds = db.DataSources.Add(strDataSourceName, strDataSourceName);  
        ds.ConnectionString = strConnectionString;  
  
        // Send the data source definition to the server.  
        ds.Update();  
  
        return ds.Name;  
}  
```  
  
##  <a name="DSV"></a> Oggetti DataSourceView  
 L'oggetto <xref:Microsoft.AnalysisServices.DataSourceView> consente di memorizzare il modello dello schema per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Affinché l'oggetto <xref:Microsoft.AnalysisServices.DataSourceView> memorizzi lo schema, è necessario innanzitutto che quest'ultimo venga creato. Gli schemi vengono creati sulla base di oggetti DataSet disponibili nello spazio dei nomi System.Data.  
  
 Nel codice di esempio seguente verrà creata parte dello schema inclusa nel progetto di esempio di Analysis Services basato su AdventureWorks. Nell'esempio vengono create definizioni dello schema per tabelle, colonne calcolate, relazioni e relazioni composte. Gli schemi sono set di dati persistenti.  
  
 Nel codice di esempio vengono eseguite le operazioni seguenti:  
  
1.  Creazione di un oggetto <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
     Verificare innanzitutto se il <xref:Microsoft.AnalysisServices.DataSource> oggetto esiste; se **true**, quindi rilasciare il <xref:Microsoft.AnalysisServices.DataSource> e crearne una. Se l'oggetto <xref:Microsoft.AnalysisServices.DataSource> non esiste, viene creato.  
  
2.  Apertura di una connessione al database tramite la stringa di connessione definita da <xref:Microsoft.AnalysisServices.DataSource>.  
  
3.  Creazione dello schema.  
  
     Lo schema è costituito dagli elementi seguenti:  
  
    -   Definizione di tabella e metodo `AddTable()`.  
  
    -   Set facoltativo di colonne calcolate e metodo `AddComputedColumn()`.  
  
    -   Set facoltativo di relazioni e metodo `AddRelation`.  
  
    -   Set facoltativo di relazioni composte e metodo `AddCompositeRelations`.  
  
4.  Aggiornamento del server.  
  
> [!NOTE]  
>  Il codice di esempio seguente è stato abbreviato per una migliore leggibilità, ma il codice completo è disponibile alla fine di questo argomento.  
  
> [!NOTE]  
>  Nel codice di esempio seguente vengono utilizzati i metodi `AddTable`, `AddComputedColumn`, `AddRelation` e `AddCompositeRelation`.  
  
> [!NOTE]  
>  La clausola `'WHERE 1=0'` consiste nell'evitare che la query restituisca righe per il **DataSet** oggetto.  
  
```  
        static DataSourceView CreateDataSourceView(Database db, string strDataSourceName)  
        {  
            // Create the data source view  
            DataSourceView dsv = db.DataSourceViews.FindByName(strDataSourceName);  
            if ( dsv != null)  
               dsv.Drop();  
            dsv = db.DataSourceViews.Add(strDataSourceName);  
            dsv.DataSourceID = strDataSourceName;  
            dsv.Schema = new DataSet();  
            dsv.Schema.Locale = CultureInfo.CurrentCulture;  
  
            // Open a connection to the data source  
            OleDbConnection connection  
                = new OleDbConnection(dsv.DataSource.ConnectionString);  
            connection.Open();  
  
            #region Create tables  
  
            // Add the DimTime table  
            AddTable(dsv, connection, "DimTime");  
            AddComputedColumn(dsv, connection, "DimTime", "SimpleDate", "DATENAME(mm, FullDateAlternateKey) + ' ' + DATENAME(dd, FullDateAlternateKey) + ',' + ' ' + DATENAME(yy, FullDateAlternateKey)");  
  
            // Add the DimProductCategory table  
            AddTable(dsv, connection, "DimProductCategory");  
  
            // Add the DimProductSubcategory table  
            AddTable(dsv, connection, "DimProductSubcategory");  
            AddRelation(dsv, "DimProductSubcategory", "ProductCategoryKey", "DimProductCategory", "ProductCategoryKey");  
  
            // Add the FactInternetSales table  
            AddTable(dsv, connection, "FactInternetSales");  
"DimTime", "TimeKey");  
            AddRelation(dsv, "FactInternetSales", "ShipDateKey", "DimTime", "TimeKey");  
            AddRelation(dsv, "FactInternetSales", "DueDateKey", "DimTime", "TimeKey");  
  
            // Add the FactInternetSalesReason table  
            AddTable(dsv, connection, "FactInternetSalesReason");  
            AddCompositeRelation(dsv, "FactInternetSalesReason", "FactInternetSales", "SalesOrderNumber", "SalesOrderLineNumber");  
            dsv.Update();  
  
            #endregion  
  
            // Send the data source view definition to the server  
            dsv.Update();  
  
            return dsv;  
        }  
  
        static void AddTable(DataSourceView dsv, OleDbConnection connection, String tableName)  
        {  
            string strSelectText = "SELECT * FROM [dbo].[" + tableName + "] WHERE 1=0";  
            OleDbDataAdapter adapter = new OleDbDataAdapter(strSelectText, connection);  
            DataTable[] dataTables = adapter.FillSchema(dsv.Schema,  
                SchemaType.Mapped, tableName);  
            DataTable dataTable = dataTables[0];  
  
            dataTable.ExtendedProperties.Add("TableType", "Table");  
            dataTable.ExtendedProperties.Add("DbSchemaName", "dbo");  
            dataTable.ExtendedProperties.Add("DbTableName", tableName);  
            dataTable.ExtendedProperties.Add("FriendlyName", tableName);  
  
            dataTable = null;  
            dataTables = null;  
            adapter = null;  
        }  
  
        static void AddComputedColumn(DataSourceView dsv, OleDbConnection connection, String tableName, String computedColumnName, String expression)  
        {  
            DataSet tmpDataSet = new DataSet();  
            tmpDataSet.Locale = CultureInfo.CurrentCulture;  
            OleDbDataAdapter adapter = new OleDbDataAdapter("SELECT ("  
                + expression + ") AS [" + computedColumnName + "] FROM [dbo].["  
                + tableName + "] WHERE 1=0", connection);  
            DataTable[] dataTables = adapter.FillSchema(tmpDataSet,  
                SchemaType.Mapped, tableName);  
            DataTable dataTable = dataTables[0];  
            DataColumn dataColumn = dataTable.Columns[computedColumnName];  
  
            dataTable.Constraints.Clear();  
            dataTable.Columns.Remove(dataColumn);  
  
            dataColumn.ExtendedProperties.Add("DbColumnName", computedColumnName);  
            dataColumn.ExtendedProperties.Add("ComputedColumnExpression",  
                expression);  
            dataColumn.ExtendedProperties.Add("IsLogical", "True");  
  
            dsv.Schema.Tables[tableName].Columns.Add(dataColumn);  
  
            dataColumn = null;  
            dataTable = null;  
            dataTables = null;  
            adapter = null;  
            tmpDataSet = null;  
        }  
  
        static void AddRelation(DataSourceView dsv, String fkTableName, String fkColumnName, String pkTableName, String pkColumnName)  
        {  
            DataColumn fkColumn  
                = dsv.Schema.Tables[fkTableName].Columns[fkColumnName];  
            DataColumn pkColumn  
                = dsv.Schema.Tables[pkTableName].Columns[pkColumnName];  
            dsv.Schema.Relations.Add("FK_" + fkTableName + "_"  
                + fkColumnName, pkColumn, fkColumn, true);  
        }  
  
        static void AddCompositeRelation(DataSourceView dsv, String fkTableName, String pkTableName, String columnName1, String columnName2)  
        {  
            DataColumn[] fkColumns = new DataColumn[2];  
            fkColumns[0] = dsv.Schema.Tables[fkTableName].Columns[columnName1];  
            fkColumns[1] = dsv.Schema.Tables[fkTableName].Columns[columnName2];  
  
            DataColumn[] pkColumns = new DataColumn[2];  
            pkColumns[0] = dsv.Schema.Tables[pkTableName].Columns[columnName1];  
            pkColumns[1] = dsv.Schema.Tables[pkTableName].Columns[columnName2];  
  
            dsv.Schema.Relations.Add("FK_" + fkTableName + "_" + columnName1  
                + "_" + columnName2, pkColumns, fkColumns, true);  
        }  
  
```  
  
 Nell'esempio di codice, il `AddTable` e `AddComputedColumn` metodi utilizzano il `FillSchema` metodo il **DataAdapter** oggetto da aggiungere un **DataTable** per un **DataSet**e configurare lo schema affinché corrisponda a quello nell'origine dati. Le proprietà estese aggiungono le informazioni necessarie per configurare lo schema per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Nel codice di esempio i metodi `AddRelation` e `AddCompositeRelation` aggiungono le colonne della relazione in base allo schema esistente e alle colonne esistenti nel modello. Per il corretto funzionamento dei metodi, le colonne devono far parte delle tabelle definite nello schema.  
  
 Di seguito viene riportato l'esempio di codice completo:  
  
```  
static DataSourceView CreateDataSourceView(Database db, string strDataSourceName)  
{  
    // Create the data source view  
    DataSourceView dsv = db.DataSourceViews.FindByName(strDataSourceName);  
    if ( dsv != null)  
       dsv.Drop();  
    dsv = db.DataSourceViews.Add(strDataSourceName);  
    dsv.DataSourceID = strDataSourceName;  
    dsv.Schema = new DataSet();  
    dsv.Schema.Locale = CultureInfo.CurrentCulture;  
  
    // Open a connection to the data source  
    OleDbConnection connection  
        = new OleDbConnection(dsv.DataSource.ConnectionString);  
    connection.Open();  
  
    #region Create tables  
  
    // Add the DimTime table  
    AddTable(dsv, connection, "DimTime");  
    AddComputedColumn(dsv, connection, "DimTime", "SimpleDate", "DATENAME(mm, FullDateAlternateKey) + ' ' + DATENAME(dd, FullDateAlternateKey) + ',' + ' ' + DATENAME(yy, FullDateAlternateKey)");  
    AddComputedColumn(dsv, connection, "DimTime", "CalendarYearDesc", "'CY' + ' ' + CalendarYear");  
    AddComputedColumn(dsv, connection, "DimTime", "CalendarSemesterDesc", "CASE WHEN CalendarSemester = 1 THEN 'H1'+' '+ 'CY' +' '+ CONVERT(CHAR (4), CalendarYear) ELSE 'H2'+' '+ 'CY' +' '+ CONVERT(CHAR (4), CalendarYear) END");  
    AddComputedColumn(dsv, connection, "DimTime", "CalendarQuarterDesc", "'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY' +' '+ CONVERT(CHAR (4), CalendarYear)");  
    AddComputedColumn(dsv, connection, "DimTime", "MonthName", "EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalYearDesc", "'FY' + ' ' + FiscalYear");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalSemesterDesc", "CASE WHEN FiscalSemester = 1 THEN 'H1'+' '+ 'FY' +' '+ CONVERT(CHAR (4), FiscalYear) ELSE 'H2'+' '+ 'FY' +' '+ CONVERT(CHAR (4), FiscalYear) END");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalQuarterDesc", "'Q' + CONVERT(CHAR (1), FiscalQuarter) +' '+ 'FY' +' '+ CONVERT(CHAR (4), FiscalYear)");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalMonthNumberOfYear", "CASE WHEN MonthNumberOfYear = '1'  THEN CONVERT(int,'7') WHEN MonthNumberOfYear = '2'  THEN CONVERT(int,'8') WHEN MonthNumberOfYear = '3'  THEN CONVERT(int,'9') WHEN MonthNumberOfYear = '4'  THEN CONVERT(int,'10') WHEN MonthNumberOfYear = '5'  THEN CONVERT(int,'11') WHEN MonthNumberOfYear = '6'  THEN CONVERT(int,'12') WHEN MonthNumberOfYear = '7'  THEN CONVERT(int,'1') WHEN MonthNumberOfYear = '8'  THEN CONVERT(int,'2') WHEN MonthNumberOfYear = '9'  THEN CONVERT(int,'3') WHEN MonthNumberOfYear = '10' THEN CONVERT(int,'4') WHEN MonthNumberOfYear = '11' THEN CONVERT(int,'5') WHEN MonthNumberOfYear = '12' THEN CONVERT(int,'6') END");  
    dsv.Update();  
  
    // Add the DimGeography table  
    AddTable(dsv, connection, "DimGeography");  
  
    // Add the DimProductCategory table  
    AddTable(dsv, connection, "DimProductCategory");  
  
    // Add the DimProductSubcategory table  
    AddTable(dsv, connection, "DimProductSubcategory");  
    AddRelation(dsv, "DimProductSubcategory", "ProductCategoryKey", "DimProductCategory", "ProductCategoryKey");  
  
    // Add the DimProduct table  
    AddTable(dsv, connection, "DimProduct");  
    AddComputedColumn(dsv, connection, "DimProduct", "ProductLineName", "CASE ProductLine WHEN 'M' THEN 'Mountain' WHEN 'R' THEN 'Road' WHEN 'S' THEN 'Accessory' WHEN 'T' THEN 'Touring' ELSE 'Components' END");  
    AddRelation(dsv, "DimProduct", "ProductSubcategoryKey", "DimProductSubcategory", "ProductSubcategoryKey");  
    dsv.Update();  
  
    // Add the DimCustomer table  
    AddTable(dsv, connection, "DimCustomer");  
    AddComputedColumn(dsv, connection, "DimCustomer", "FullName", "CASE WHEN MiddleName IS NULL THEN FirstName + ' ' + LastName ELSE FirstName + ' ' + MiddleName + ' ' + LastName END");  
    AddComputedColumn(dsv, connection, "DimCustomer", "GenderDesc", "CASE WHEN Gender = 'M' THEN 'Male' ELSE 'Female' END");  
    AddComputedColumn(dsv, connection, "DimCustomer", "MaritalStatusDesc", "CASE WHEN MaritalStatus = 'S' THEN 'Single' ELSE 'Married' END");  
    AddRelation(dsv, "DimCustomer", "GeographyKey", "DimGeography", "GeographyKey");  
  
    // Add the DimReseller table  
    AddTable(dsv, connection, "DimReseller");  
    AddComputedColumn(dsv, connection, "DimReseller", "OrderFrequencyDesc", "CASE WHEN OrderFrequency = 'A' THEN 'Annual' WHEN OrderFrequency = 'S' THEN 'Bi-Annual' ELSE 'Quarterly' END");  
    AddComputedColumn(dsv, connection, "DimReseller", "OrderMonthDesc", "CASE WHEN OrderMonth = '1' THEN 'January' WHEN OrderMonth = '2' THEN 'February' WHEN OrderMonth = '3' THEN 'March' WHEN OrderMonth = '4' THEN 'April' WHEN OrderMonth = '5' THEN 'May' WHEN OrderMonth = '6' THEN 'June' WHEN OrderMonth = '7' THEN 'July' WHEN OrderMonth = '8' THEN 'August' WHEN OrderMonth = '9' THEN 'September' WHEN OrderMonth = '10' THEN 'October' WHEN OrderMonth = '11' THEN 'November' WHEN OrderMonth = '12' THEN 'December' ELSE 'Never Ordered' END");  
  
    // Add the DimCurrency table  
    AddTable(dsv, connection, "DimCurrency");  
    dsv.Update();  
  
    // Add the DimSalesReason table  
    AddTable(dsv, connection, "DimSalesReason");  
  
    // Add the FactInternetSales table  
    AddTable(dsv, connection, "FactInternetSales");  
    AddRelation(dsv, "FactInternetSales", "ProductKey", "DimProduct", "ProductKey");  
    AddRelation(dsv, "FactInternetSales", "CustomerKey", "DimCustomer", "CustomerKey");  
    AddRelation(dsv, "FactInternetSales", "OrderDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactInternetSales", "ShipDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactInternetSales", "DueDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactInternetSales", "CurrencyKey", "DimCurrency", "CurrencyKey");  
    dsv.Update();  
  
    // Add the FactResellerSales table  
    AddTable(dsv, connection, "FactResellerSales");  
    AddRelation(dsv, "FactResellerSales", "ProductKey", "DimProduct", "ProductKey");  
    AddRelation(dsv, "FactResellerSales", "ResellerKey", "DimReseller", "ResellerKey");  
    AddRelation(dsv, "FactResellerSales", "OrderDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactResellerSales", "ShipDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactResellerSales", "DueDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactResellerSales", "CurrencyKey", "DimCurrency", "CurrencyKey");  
  
    // Add the FactInternetSalesReason table  
    AddTable(dsv, connection, "FactInternetSalesReason");  
    AddCompositeRelation(dsv, "FactInternetSalesReason", "FactInternetSales", "SalesOrderNumber", "SalesOrderLineNumber");  
    dsv.Update();  
  
    // Add the FactCurrencyRate table  
    AddTable(dsv, connection, "FactCurrencyRate");  
    AddRelation(dsv, "FactCurrencyRate", "CurrencyKey", "DimCurrency", "CurrencyKey");  
    AddRelation(dsv, "FactCurrencyRate", "TimeKey", "DimTime", "TimeKey");  
  
    #endregion  
  
    // Send the data source view definition to the server  
    dsv.Update();  
  
    return dsv;  
}  
  
static void AddTable(DataSourceView dsv, OleDbConnection connection, String tableName)  
{  
    string strSelectText = "SELECT * FROM [dbo].[" + tableName + "] WHERE 1=0";  
    OleDbDataAdapter adapter = new OleDbDataAdapter(strSelectText, connection);  
    DataTable[] dataTables = adapter.FillSchema(dsv.Schema,  
        SchemaType.Mapped, tableName);  
    DataTable dataTable = dataTables[0];  
  
    dataTable.ExtendedProperties.Add("TableType", "Table");  
    dataTable.ExtendedProperties.Add("DbSchemaName", "dbo");  
    dataTable.ExtendedProperties.Add("DbTableName", tableName);  
    dataTable.ExtendedProperties.Add("FriendlyName", tableName);  
  
    dataTable = null;  
    dataTables = null;  
    adapter = null;  
}  
  
static void AddComputedColumn(DataSourceView dsv, OleDbConnection connection, String tableName, String computedColumnName, String expression)  
{  
    DataSet tmpDataSet = new DataSet();  
    tmpDataSet.Locale = CultureInfo.CurrentCulture;  
    OleDbDataAdapter adapter = new OleDbDataAdapter("SELECT ("  
        + expression + ") AS [" + computedColumnName + "] FROM [dbo].["  
        + tableName + "] WHERE 1=0", connection);  
    DataTable[] dataTables = adapter.FillSchema(tmpDataSet,  
        SchemaType.Mapped, tableName);  
    DataTable dataTable = dataTables[0];  
    DataColumn dataColumn = dataTable.Columns[computedColumnName];  
  
    dataTable.Constraints.Clear();  
    dataTable.Columns.Remove(dataColumn);  
  
    dataColumn.ExtendedProperties.Add("DbColumnName", computedColumnName);  
    dataColumn.ExtendedProperties.Add("ComputedColumnExpression",  
        expression);  
    dataColumn.ExtendedProperties.Add("IsLogical", "True");  
  
    dsv.Schema.Tables[tableName].Columns.Add(dataColumn);  
  
    dataColumn = null;  
    dataTable = null;  
    dataTables = null;  
    adapter = null;  
    tmpDataSet = null;  
}  
  
static void AddRelation(DataSourceView dsv, String fkTableName, String fkColumnName, String pkTableName, String pkColumnName)  
{  
    DataColumn fkColumn  
        = dsv.Schema.Tables[fkTableName].Columns[fkColumnName];  
    DataColumn pkColumn  
        = dsv.Schema.Tables[pkTableName].Columns[pkColumnName];  
    dsv.Schema.Relations.Add("FK_" + fkTableName + "_"  
        + fkColumnName, pkColumn, fkColumn, true);  
}  
  
static void AddCompositeRelation(DataSourceView dsv, String fkTableName, String pkTableName, String columnName1, String columnName2)  
{  
    DataColumn[] fkColumns = new DataColumn[2];  
    fkColumns[0] = dsv.Schema.Tables[fkTableName].Columns[columnName1];  
    fkColumns[1] = dsv.Schema.Tables[fkTableName].Columns[columnName2];  
  
    DataColumn[] pkColumns = new DataColumn[2];  
    pkColumns[0] = dsv.Schema.Tables[pkTableName].Columns[columnName1];  
    pkColumns[1] = dsv.Schema.Tables[pkTableName].Columns[columnName2];  
  
    dsv.Schema.Relations.Add("FK_" + fkTableName + "_" + columnName1  
        + "_" + columnName2, pkColumns, fkColumns, true);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [Architettura logica & #40; Analysis Services - dati multidimensionali & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database & #40; Analysis Services - dati multidimensionali & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
