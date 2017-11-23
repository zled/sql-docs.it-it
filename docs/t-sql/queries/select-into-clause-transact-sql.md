---
title: NELLA clausola (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INTO_TSQL
- INSERT_INTO_TSQL
- INSERT INTO
- INTO
- INTO clause
- INTO_clause_TSQL
dev_langs: TSQL
helpviewer_keywords:
- copying data [SQL Server], into a new table
- INTO clause
- moving data, to a new table
- table creation [SQL Server], INTO clause
- SELECT INTO statement
- inserting rows
- clauses [SQL Server], INTO
- row additions [SQL Server], INTO clause
ms.assetid: b48d69e8-5a00-48bf-b2f3-19278a72dd88
caps.latest.revision: "63"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: df016654700bd36ebb553e7b3cd66f50d35eadc1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="select---into-clause-transact-sql"></a>-Clausola SELECT INTO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  SELECT…INTO crea una nuova tabella nel filegroup predefinito e vi inserisce le righe restituite dalla query. Per visualizzare la sintassi SELECT completa, vedere [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ INTO new_table ]
[ ON filegroup]
```  
  
## <a name="arguments"></a>Argomenti  
 *new_table*  
 Specifica il nome di una nuova tabella da creare in base alle colonne dell'elenco di selezione e alle righe scelte dall'origine dati.  
 
  *filegroup*
 
 Specifica il nome del filegroup in cui verrà creata la tabella nuova. Il filegroup specificato deve esistere nel database else di genera un'eccezione il motore di SQL Server un errore. Questa opzione è supportata solo a partire da [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].
 
 Il formato di *new_table* viene determinato valutando le espressioni nell'elenco di selezione. Le colonne in *new_table* vengono creati nell'ordine specificato dall'elenco di selezione. Ogni colonna *new_table* ha lo stesso nome, tipo di dati, ammissione di valori null e valore dell'espressione corrispondente nell'elenco di selezione. La proprietà IDENTITY di una colonna viene trasferita, tranne nelle condizioni definite in "Utilizzo di colonne Identity" nella sezione Osservazioni.  
  
 Per creare la tabella in un altro database nella stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare *new_table* come un nome completo nel formato *TABLE_NAME*.  
  
 Non è possibile creare *new_table* in un server remoto; tuttavia, è possibile popolare *new_table* da un'origine dati remota. Per creare *new_table* da una tabella di origine remota, specificare la tabella di origine utilizzando un nome composto da quattro parti nel formato *server_collegato*. *catalogo*. *schema*. *oggetto* nella clausola FROM dell'istruzione SELECT. In alternativa, è possibile utilizzare il [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) funzione o [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) funzione nella clausola FROM per specificare l'origine dati remota.  
  
## <a name="data-types"></a>Tipi di dati  
 L'attributo FILESTREAM non viene trasferito nella nuova tabella. Oggetti BLOB FILESTREAM vengono copiati e archiviati nella nuova tabella come **varbinary (max)** BLOB. Senza l'attributo FILESTREAM, il **varbinary (max)** tipo di dati è limitata a 2 GB. Se un oggetto BLOB FILESTREAM supera questo valore, viene generato l'errore 7119 e l'istruzione viene arrestata.  
  
 Quando viene selezionata una colonna Identity esistente in una nuova tabella, la nuova colonna eredita la proprietà IDENTITY, a meno che non si verifichi una delle seguenti condizioni:  
  
-   L'istruzione SELECT contiene un join.  
  
-   Più istruzioni SELECT sono unite in join tramite l'operatore UNION.  
  
-   La colonna Identity è inclusa più di una volta nell'elenco di selezione.  
  
-   La colonna Identity fa parte di un'espressione.  
  
-   La colonna Identity proviene da un'origine dei dati remota.  
  
Se una di queste condizioni risulta vera, la colonna viene creata come colonna NOT NULL, anziché ereditare la proprietà IDENTITY. Se una colonna Identity è richiesta nella nuova tabella ma tale colonna non è disponibile o si desidera un valore di inizializzazione o di incremento diverso della colonna Identity di origine, definire la colonna nell'elenco di selezione utilizzando la funzione IDENTITY. Vedere "Creazione di una colonna Identity tramite la funzione IDENTITY" nella sezione Esempi più avanti.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Non è possibile specificare una variabile di tabella o un parametro con valori di tabella come nuova tabella.  
  
 Non è possibile utilizzare SELECT…INTO per creare una tabella partizionata, anche quando la tabella di origine è partizionata. Lo schema di partizione della tabella di origine non viene utilizzato in SELECT...INTO. La nuova tabella viene invece creata nel filegroup predefinito. Per inserire righe in una tabella partizionata, per prima cosa è necessario creare la tabella partizionata, quindi utilizzare l'istruzione INSERT INTO...SELECT FROM.  
  
 Indici, vincoli e trigger definiti nella tabella di origine non vengono trasferiti alla nuova tabella e non possono essere specificati nell'istruzione SELECT...INTO. Se questi oggetti sono richiesti, è possibile crearli dopo avere eseguito l'istruzione SELECT...INTO.  
  
 La specifica della clausola ORDER BY non garantisce che le righe vengano inserite nell'ordine specificato.  
  
 Quando nell'elenco di selezione è presente una colonna di tipo sparse, la relativa proprietà non viene trasferita nella colonna della nuova tabella. Se questa proprietà è richiesta nella nuova tabella, modificare la definizione di colonna dopo l'esecuzione dell'istruzione SELECT...INTO per includere la proprietà.  
  
 Quando nell'elenco di selezione è presente una colonna calcolata, la colonna corrispondente della nuova tabella non è di tipo calcolato. I valori della nuova colonna corrispondono ai valori calcolati quando è stata eseguita l'istruzione SELECT...INTO.  
  
## <a name="logging-behavior"></a>Comportamento di registrazione  
 La quantità di registrazioni per SELECT INTO dipende dal modello di recupero attivato per il database. Nel modello di recupero con registrazione minima o in quello con registrazione minima delle operazioni bulk, per tali operazioni la registrazione prevista è quella minima. Con registrazione minima, utilizzando l'istruzione SELECT... UN'istruzione può essere più efficiente rispetto alla creazione di una tabella e quindi popolamento della tabella con un'istruzione INSERT. Per altre informazioni, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
## <a name="permissions"></a>Permissions  
 È necessaria l'autorizzazione CREATE TABLE nel database di destinazione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-table-by-specifying-columns-from-multiple-sources"></a>A. Creazione di una tabella specificando colonne provenienti da più origini  
 Nell'esempio seguente viene creata la tabella `dbo.EmployeeAddresses` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] selezionando sette colonne da diverse tabelle relative a dipendenti e indirizzi.  
  
```tsql  
SELECT c.FirstName, c.LastName, e.JobTitle, a.AddressLine1, a.City,   
    sp.Name AS [State/Province], a.PostalCode  
INTO dbo.EmployeeAddresses  
FROM Person.Person AS c  
    JOIN HumanResources.Employee AS e   
    ON e.BusinessEntityID = c.BusinessEntityID  
    JOIN Person.BusinessEntityAddress AS bea  
    ON e.BusinessEntityID = bea.BusinessEntityID  
    JOIN Person.Address AS a  
    ON bea.AddressID = a.AddressID  
    JOIN Person.StateProvince as sp   
    ON sp.StateProvinceID = a.StateProvinceID;  
GO  
```  
  
### <a name="b-inserting-rows-using-minimal-logging"></a>B. Inserimento di righe utilizzando la registrazione minima  
 Nell'esempio seguente viene creata la tabella `dbo.NewProducts`, in cui vengono inserite righe della tabella `Production.Product`. L'esempio presuppone che il modello di recupero del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sia impostato su FULL. Per assicurare l'utilizzo della registrazione minima, il modello di recupero del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] viene impostato su BULK_LOGGED prima che le righe vengano inserite e reimpostato su FULL dopo l'istruzione SELECT...INTO. In tal modo, si assicura l'utilizzo da parte dell'istruzione SELECT...INTO di uno spazio minimo nel log delle transazioni con risultati efficienti.  
  
```tsql  
ALTER DATABASE AdventureWorks2012 SET RECOVERY BULK_LOGGED;  
GO  
  
SELECT * INTO dbo.NewProducts  
FROM Production.Product  
WHERE ListPrice > $25   
AND ListPrice < $100;  
GO  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
GO  
```  
  
### <a name="c-creating-an-identity-column-using-the-identity-function"></a>C. Creazione di una colonna Identity tramite la funzione IDENTITY  
 Nell'esempio seguente viene utilizzata la funzione IDENTITY per creare una colonna Identity nella nuova tabella `Person.USAddress` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Questa operazione è necessaria perché l'istruzione SELECT che definisce la tabella contiene un join che fa in modo che la proprietà IDENTITY non venga trasferita nella nuova tabella. Si noti che il valore di inizializzazione e il valore di incremento specificati nella funzione IDENTITY sono diversi da quelli della colonna `AddressID` nella tabella di origine `Person.Address`.  
  
```tsql  
-- Determine the IDENTITY status of the source column AddressID.  
SELECT OBJECT_NAME(object_id) AS TableName, name AS column_name, 
  is_identity, seed_value, increment_value  
FROM sys.identity_columns  
WHERE name = 'AddressID';  
  
-- Create a new table with columns from the existing table Person.Address. 
-- A new IDENTITY column is created by using the IDENTITY function.  
SELECT IDENTITY (int, 100, 5) AS AddressID,   
       a.AddressLine1, a.City, b.Name AS State, a.PostalCode  
INTO Person.USAddress   
FROM Person.Address AS a  
INNER JOIN Person.StateProvince AS b 
  ON a.StateProvinceID = b.StateProvinceID  
WHERE b.CountryRegionCode = N'US';   
  
-- Verify the IDENTITY status of the AddressID columns in both tables.  
SELECT OBJECT_NAME(object_id) AS TableName, name AS column_name, 
  is_identity, seed_value, increment_value  
FROM sys.identity_columns  
WHERE name = 'AddressID';  
```  
  
### <a name="d-creating-a-table-by-specifying-columns-from-a-remote-data-source"></a>D. Creazione di una tabella specificando colonne provenienti da un'origine dei dati remota  
 Nell'esempio seguente vengono illustrati tre metodi per creare una nuova tabella nel server locale da un'origine dati remota. L'esempio inizia con la creazione di un collegamento all'origine dati remota. Il nome del server collegato, `MyLinkServer,` viene specificato nella clausola FROM della prima istruzione SELECT...INTO e nella funzione OPENQUERY della seconda istruzione SELECT...INTO. La terza istruzione SELECT...INTO utilizza la funzione OPENDATASOURCE che specifica direttamente l'origine dei dati remota anziché utilizzare il nome del server collegato.  
  
 **Si applica a:** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' 
-- or 'server_name\instance_name'.  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI',   
    @datasrc = N'server_name',  
    @catalog = N'AdventureWorks2012';  
GO  

USE AdventureWorks2012;  
GO  
-- Specify the remote data source in the FROM clause using a four-part name   
-- in the form linked_server.catalog.schema.object.  
SELECT DepartmentID, Name, GroupName, ModifiedDate  
INTO dbo.Departments  
FROM MyLinkServer.AdventureWorks2012.HumanResources.Department  
GO  
-- Use the OPENQUERY function to access the remote data source.  
SELECT DepartmentID, Name, GroupName, ModifiedDate  
INTO dbo.DepartmentsUsingOpenQuery  
FROM OPENQUERY(MyLinkServer, 'SELECT *  
               FROM AdventureWorks2012.HumanResources.Department');   
GO  
-- Use the OPENDATASOURCE function to specify the remote data source.  
-- Specify a valid server name for Data Source using the format 
-- server_name or server_name\instance_name.  
SELECT DepartmentID, Name, GroupName, ModifiedDate  
INTO dbo.DepartmentsUsingOpenDataSource  
FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source=server_name;Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Department;  
GO  
```  
  
### <a name="e-import-from-an-external-table-created-with--polybase"></a>E. Importare da una tabella esterna creata con PolyBase  
 Importare dati da Hadoop o dall'archiviazione di Azure in SQL Server per l'archivio permanente. Utilizzare `SELECT INTO` per importare i dati a cui fa riferimento una tabella esterna per l'archivio permanente in SQL Server. Creare un tabella relazionale e quindi creare un indice di archivio colonne nella parte superiore della tabella in un secondo passaggio.  
  
 **Si applica a:** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql
-- Import data for car drivers into SQL Server to do more in-depth analysis.  
SELECT DISTINCT   
        Insured_Customers.FirstName, Insured_Customers.LastName,   
        Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
INTO Fast_Customers from Insured_Customers INNER JOIN   
(  
        SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
ORDER BY YearlyIncome  
  
```  
### <a name="f-creating-a-new-table-as-a-copy-of-another-table-and-loading-it-a-specified-filegroup"></a>F. Crea una nuova tabella come copia di un'altra tabella e caricamento di un filegroup specificato
Il seguente esempio viene illustrato la creazione di una nuova tabella come copia di un'altra tabella e caricarli in un filegroup specificato diverso dal filegroup predefinito dell'utente.

 **Si applica a:**[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]

```tsql
ALTER DATABASE [AdventureWorksDW2016] ADD FILEGROUP FG2;
ALTER DATABASE [AdventureWorksDW2016]
ADD FILE
(
NAME='FG2_Data',
FILENAME = '/var/opt/mssql/data/AdventureWorksDW2016_Data1.mdf'
)
TO FILEGROUP FG2;
GO
SELECT *  INTO [dbo].[FactResellerSalesXL] ON FG2 from [dbo].[FactResellerSales]
```
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Selezionare esempi &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [IDENTITÀ &#40; Funzione &#41; &#40; Transact-SQL &#41;](../../t-sql/functions/identity-function-transact-sql.md)  
  
  
