---
title: Spiegare (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4846a576-57ea-4068-959c-81e69e39ddc1
caps.latest.revision: 13
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: af61ec5c670bdc48a3f661080983fac3e7263014
ms.contentlocale: it-it
ms.lasthandoff: 10/24/2017

---
# <a name="explain-transact-sql"></a>Spiegare (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Restituisce il piano di query per un [!INCLUDE[ssDW](../../includes/ssdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] istruzione senza eseguire l'istruzione. Utilizzare **ESPLICATIVO** per le operazioni che richiede lo spostamento dei dati di anteprima e visualizzare i costi stimati delle operazioni di query.  
  
 Per ulteriori informazioni sui piani di query, vedere "Informazioni sui piani di Query" nel [!INCLUDE[pdw-product-documentation_md](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  

```  
EXPLAIN SQL_statement  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SQL_statement*  
 Il [!INCLUDE[DWsql](../../includes/dwsql-md.md)] istruzione in cui **ESPLICATIVO** verrà eseguito. *SQL_statement* può essere uno dei seguenti comandi: **selezionare**, **inserire**, **aggiornamento**, **eliminare**,  **CREATE TABLE AS SELECT**, **crea una tabella remota**.  
  
## <a name="permissions"></a>Permissions  
 Richiede il **SHOWPLAN** autorizzazione e dell'autorizzazione per eseguire *SQL_statement*. Vedere [autorizzazioni: GRANT, DENY, REVOKE &#40; Azure SQL Data Warehouse, Parallel Data Warehouse &#41; ](../../t-sql/statements/permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse.md).  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito dal **ESPLICATIVO** comando è un documento XML con la struttura illustrato di seguito. Questo documento XML vengono elencate tutte le operazioni nel piano di query per una determinata query, ognuno racchiuso il `<dsql_operation>` tag. Il valore restituito è di tipo **nvarchar (max)**.  
  
 Il piano di query restituita illustra sequenziale istruzioni SQL. Quando viene eseguita la query può implicare parallelizzate operazioni, in modo alcune istruzioni sequenziale visualizzate possono essere eseguite nello stesso momento.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<dsql_query>  
  <sql>. . .</sql>  
  <params />  
  <dsql_operations>  
    <dsql_operation>  
     . . .      
    </dsql_operation>  
    [ . . . n ]  
  <dsql_operations>  
</dsql_query>  
```  
  
 I tag XML contengono queste informazioni:  
  
|(Tag XML)|Riepilogo, attributi e contenuto|  
|-------------|--------------------------------------|  
|\<dsql_query >|Elemento di livello superiore o documento.|
|\<SQL >|Esegue l'eco del *SQL_statement*.|  
|\<params >|Questo tag non viene usato in questo momento.|  
|\<dsql_operations >|Vengono riepilogati e contiene i passaggi di query e include informazioni sui costi per la query. Contiene anche tutte le `<dsql_operation>` blocchi. Il tag contiene informazioni relative al conteggio per l'intera query:<br /><br /> `<dsql_operations total_cost=total_cost total_number_operations=total_number_operations>`<br /><br /> *total_cost* il tempo stimato per la query da eseguire, in millisecondi.<br /><br /> *total_number_operations* è il numero totale di operazioni per la query. Un'operazione che verrà eseguito in parallelo ed eseguire su più nodi viene conteggiata come una singola operazione.|  
|\<dsql_operation >|Descrive una singola operazione all'interno del piano di query. Il \<dsql_operation > tag contiene il tipo di operazione come attributo:<br /><br /> `<dsql_operation operation_type=operation_type>`<br /><br /> *operation_type* è uno dei valori disponibili nel [query su dati (SQL Server PDW)](http://msdn.microsoft.com/en-us/3f4f5643-012a-4c36-b5ec-691c4bbe668c).<br /><br /> Il contenuto di `\<dsql_operation>` blocco dipende dal tipo di operazione.<br /><br /> Vedere la tabella riportata di seguito.|  
  
|Tipo di operazione|Contenuto|Esempio|  
|--------------------|-------------|-------------|  
|BROADCAST_MOVE, DISTRIBUTE_REPLICATED_TABLE_MOVE, MASTER_TABLE_MOVE, PARTITION_MOVE, SHUFFLE_MOVE e TRIM_MOVE|`<operation_cost>`elemento, con questi attributi. I valori riflettono solo l'operazione locale:<br /><br /> -   *costo* è il costo dell'operatore locale e Mostra il tempo stimato per l'operazione da eseguire, in millisecondi.<br />-   *accumulative_cost* è la somma di tutte le operazioni visualizzate nel piano inclusi i valori sommati di operazioni parallele, in ms.<br />-   *average_rowsize* le dimensioni medie delle righe stimate (in byte) di righe recuperato e passato durante l'operazione.<br />-   *output_rows* è la cardinalità di output (nodo) e Mostra il numero di righe di output.<br /><br /> `<location>`: I nodi o le distribuzioni in cui si verificherà l'operazione. Le opzioni sono: "Controllo", "ComputeNode", "AllComputeNodes", "AllDistributions", "SubsetDistributions", "Distribuzione" e "SubsetNodes".<br /><br /> `<source_statement>`: Spostare i dati di origine per la riproduzione casuale.<br /><br /> `<destination_table>`: La tabella temporanea interna i dati verranno spostati in.<br /><br /> `<shuffle_columns>`: (Applicabile solo alle operazioni SHUFFLE_MOVE). Uno o più colonne utilizzate come colonne di distribuzione per la tabella temporanea.|`<operation_cost cost="40" accumulative_cost="40" average_rowsize = "50" output_rows="100"/>`<br /><br /> `<location distribution="AllDistributions" />`<br /><br /> `<source_statement type="statement">SELECT [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d].[dist_date] FROM [qatest].[dbo].[flyers] [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d]       </source_statement>`<br /><br /> `<destination_table>Q_[TEMP_ID_259]_[PARTITION_ID]</destination_table>`<br /><br /> `<shuffle_columns>dist_date;</shuffle_columns>`|  
|CopyOperation|`<operation_cost>`: Vedere `<operation_cost>` sopra.<br /><br /> `<DestinationCatalog>`: Il nodo di destinazione o i nodi.<br /><br /> `<DestinationSchema>`: Lo schema di destinazione in DestinationCatalog.<br /><br /> `<DestinationTableName>`: Nome della tabella di destinazione o "TableName".<br /><br /> `<DestinationDatasource>`: Le informazioni di connessione o nome per l'origine dati di destinazione.<br /><br /> `<Username>`e `<Password>`: questi campi indicano che un nome utente e una password per la destinazione potrebbe essere necessari.<br /><br /> `<BatchSize>`: La dimensione di batch per l'operazione di copia.<br /><br /> `<SelectStatement>`: L'istruzione select utilizzata per eseguire la copia.<br /><br /> `<distribution>`: La distribuzione in cui viene eseguita la copia.|`<operation_cost cost="0" accumulative_cost="0" average_rowsize="4" output_rows="1" />`<br /><br /> `<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>[TableName]</DestinationTableName>`<br /><br /> `<DestinationDatasource>localhost, 8080</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<BatchSize>6000</BatchSize>`<br /><br /> `<SelectStatement>SELECT T1_1.c1 AS c1 FROM [qatest].[dbo].[gigs] AS T1_1</SelectStatement>`<br /><br /> `<distribution>ControlNode</distribution>`|  
|MetaDataCreate_Operation|`<source_table>`: La tabella di origine per l'operazione.<br /><br /> `<destionation_table>`: La tabella di destinazione per l'operazione.|`<source_table>databases</source_table>`<br /><br /> `<destination_table>MetaDataCreateLandingTempTable</destination_table>`|  
|ON|`<location>`: Vedere `<location>` sopra.<br /><br /> `<sql_operation>`: Individua il comando SQL che verrà eseguito su un nodo.|`<location permanent="false" distribution="AllDistributions">Compute</location>`<br /><br /> `<sql_operation type="statement">CREATE TABLE [tempdb].[dbo]. [Q_[TEMP_ID_259]]_ [PARTITION_ID]]]([dist_date] DATE) WITH (DISTRIBUTION = HASH([dist_date]),) </sql_operation>`|  
|RemoteOnOperation|`<DestinationCatalog>`: Il catalogo di destinazione.<br /><br /> `<DestinationSchema>`: Lo schema di destinazione in DestinationCatalog.<br /><br /> `<DestinationTableName>`: Nome della tabella di destinazione o "TableName".<br /><br /> `<DestinationDatasource>`: Nome dell'origine dati di destinazione.<br /><br /> `<Username>`e `<Password>`: questi campi indicano che un nome utente e una password per la destinazione potrebbe essere necessari.<br /><br /> `<CreateStatement>`: L'istruzione di creazione della tabella per il database di destinazione.|`<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>TableName</DestinationTableName>`<br /><br /> `<DestinationDatasource>DestDataSource</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<CreateStatement>CREATE TABLE [master].[dbo].[TableName] ([col1] BIGINT) ON [PRIMARY] WITH(DATA_COMPRESSION=PAGE);</CreateStatement>`|  
|RETURN|`<resultset>`: L'identificatore per il set di risultati.|`<resultset>RS_19</resultset>`|  
|RND_ID|`<identifier>`: L'identificatore per l'oggetto creato.|`<identifier>TEMP_ID_260</identifier>`|  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 **Spiegare** può essere applicato a *ottimizzabili* solo query sono query che può essere migliorata o modificata in base ai risultati di un **spiegare** comando. Supportato **ESPLICATIVO** sono elencati i comandi. Tentativo di utilizzare **ESPLICATIVO** con una query non supportata tipo verrà restituito un errore o echo la query.  
  
 **Spiegare** non è supportato in una transazione utente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente un **ESPLICATIVO** comando eseguito in un **selezionare** istruzione e il risultato XML.  
  
 **Invio di un'istruzione di descrizione**  
  
 Il comando inviato per questo esempio è:  
  
```  
-- Uses AdventureWorks  
  
EXPLAIN   
    SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
        CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
        G.StateProvinceName, T.SalesTerritoryGroup  
    FROM dbo.DimGeography AS G  
    JOIN dbo.DimSalesTerritory AS T  
        ON G.SalesTerritoryKey = T.SalesTerritoryKey  
    JOIN dbo.DimCustomer AS C  
        ON G.GeographyKey = C.GeographyKey  
    JOIN dbo.FactInternetSales AS FIS  
        ON C.CustomerKey = FIS.CustomerKey  
    WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
        AND Gender = 'F'  
    GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
    ORDER BY AVG(YearlyIncome) DESC;  
GO  
```  
  
 Dopo l'esecuzione dell'istruzione con il **ESPLICATIVO** , l'opzione di scheda messaggio presenta una sola riga denominata **spiegare**e che inizia con il testo XML `\<?xml version="1.0" encoding="utf-8"?>` fare clic su XML per aprire l'intero testo in un Finestra XML. Per comprendere meglio i commenti seguenti, è necessario attivare la visualizzazione dei numeri di riga in SSDT.  
  
#### <a name="to-turn-on-line-numbers"></a>Per attivare i numeri di riga  
  
1.  Con l'output visualizzato nella **spiegare** scheda SSDT, il **strumenti** dal menu **opzioni**.  
  
2.  Espandere il **Editor di testo** , quindi espandere **XML**, quindi fare clic su **generale**.  
  
3.  Nel **visualizzazione** area controllo **i numeri di riga**.  
  
4.  Scegliere **OK**.  
  
 **Esempio di output descrizione**  
  
 Il risultato XML di **ESPLICATIVO** è con numeri di riga attivati:  
  
```  
1  \<?xml version="1.0" encoding="utf-8"?>  
2  <dsql_query>  
3    <sql>SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
4          CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
5          G.StateProvinceName, T.SalesTerritoryGroup  
6      FROM dbo.DimGeography AS G  
7      JOIN dbo.DimSalesTerritory AS T  
8          ON G.SalesTerritoryKey = T.SalesTerritoryKey  
9      JOIN dbo.DimCustomer AS C  
10          ON G.GeographyKey = C.GeographyKey  
11      JOIN dbo.FactInternetSales AS FIS  
12          ON C.CustomerKey = FIS.CustomerKey  
13      WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
14          AND Gender = 'F'  
15      GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
16      ORDER BY AVG(YearlyIncome) DESC</sql>  
17    <dsql_operations total_cost="0.926237696" total_number_operations="9">  
18      <dsql_operation operation_type="RND_ID">  
19        <identifier>TEMP_ID_16893</identifier>  
20      </dsql_operation>  
21      <dsql_operation operation_type="ON">  
22        <location permanent="false" distribution="AllComputeNodes" />  
23        <sql_operations>  
24          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16893] ([CustomerKey] INT NOT NULL, [GeographyKey] INT, [YearlyIncome] MONEY ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
25        </sql_operations>  
26      </dsql_operation>  
27      <dsql_operation operation_type="BROADCAST_MOVE">  
28        <operation_cost cost="0.121431552" accumulative_cost="0.121431552" average_rowsize="16" output_rows="31.6228" />  
29        <source_statement>SELECT [T1_1].[CustomerKey] AS [CustomerKey],  
30         [T1_1].[GeographyKey] AS [GeographyKey],  
31         [T1_1].[YearlyIncome] AS [YearlyIncome]  
32  FROM   (SELECT [T2_1].[CustomerKey] AS [CustomerKey],  
33                 [T2_1].[GeographyKey] AS [GeographyKey],  
34                 [T2_1].[YearlyIncome] AS [YearlyIncome]  
35          FROM   [AdventureWorksPDW2012].[dbo].[DimCustomer] AS T2_1  
36          WHERE  ([T2_1].[Gender] = CAST (N'F' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (1)) COLLATE Latin1_General_100_CI_AS_KS_WS)) AS T1_1</source_statement>  
37        <destination_table>[TEMP_ID_16893]</destination_table>  
38      </dsql_operation>  
39      <dsql_operation operation_type="RND_ID">  
40        <identifier>TEMP_ID_16894</identifier>  
41      </dsql_operation>  
42      <dsql_operation operation_type="ON">  
43        <location permanent="false" distribution="AllDistributions" />  
44        <sql_operations>  
45          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16894] ([StateProvinceName] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS, [SalesTerritoryGroup] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS NOT NULL, [col] BIGINT, [col1] MONEY NOT NULL, [col2] BIGINT, [col3] MONEY NOT NULL ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
46        </sql_operations>  
47      </dsql_operation>  
48      <dsql_operation operation_type="SHUFFLE_MOVE">  
49        <operation_cost cost="0.804806144" accumulative_cost="0.926237696" average_rowsize="232" output_rows="108.406" />  
50        <source_statement>SELECT [T1_1].[StateProvinceName] AS [StateProvinceName],  
51         [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
52         [T1_1].[col2] AS [col],  
53         [T1_1].[col] AS [col1],  
54         [T1_1].[col3] AS [col2],  
55         [T1_1].[col1] AS [col3]  
56  FROM   (SELECT ISNULL([T2_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col],  
57                 ISNULL([T2_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col1],  
58                 [T2_1].[StateProvinceName] AS [StateProvinceName],  
59                 [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
60                 [T2_1].[col] AS [col2],  
61                 [T2_1].[col2] AS [col3]  
62          FROM   (SELECT   COUNT_BIG([T3_2].[YearlyIncome]) AS [col],  
63                           SUM([T3_2].[YearlyIncome]) AS [col1],  
64                           COUNT_BIG(CAST ((0) AS INT)) AS [col2],  
65                           SUM([T3_2].[SalesAmount]) AS [col3],  
66                           [T3_2].[StateProvinceName] AS [StateProvinceName],  
67                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
68                  FROM     (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
69                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
70                            FROM   [AdventureWorksPDW2012].[dbo].[DimSalesTerritory] AS T4_1  
71                            WHERE  (([T4_1].[SalesTerritoryGroup] = CAST (N'North America' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (13)) COLLATE Latin1_General_100_CI_AS_KS_WS)  
72                                    OR ([T4_1].[SalesTerritoryGroup] = CAST (N'Pacific' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (7)) COLLATE Latin1_General_100_CI_AS_KS_WS))) AS T3_1  
73                           INNER JOIN  
74                           (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
75                                   [T4_2].[YearlyIncome] AS [YearlyIncome],  
76                                   [T4_2].[SalesAmount] AS [SalesAmount],  
77                                   [T4_1].[StateProvinceName] AS [StateProvinceName]  
78                            FROM   [AdventureWorksPDW2012].[dbo].[DimGeography] AS T4_1  
79                                   INNER JOIN  
80                                   (SELECT [T5_2].[GeographyKey] AS [GeographyKey],  
81                                           [T5_2].[YearlyIncome] AS [YearlyIncome],  
82                                           [T5_1].[SalesAmount] AS [SalesAmount]  
83                                    FROM   [AdventureWorksPDW2012].[dbo].[FactInternetSales] AS T5_1  
84                                           INNER JOIN  
85                                           [tempdb].[dbo].[TEMP_ID_16893] AS T5_2  
86                                           ON ([T5_1].[CustomerKey] = [T5_2].[CustomerKey])) AS T4_2  
87                                   ON ([T4_2].[GeographyKey] = [T4_1].[GeographyKey])) AS T3_2  
88                           ON ([T3_1].[SalesTerritoryKey] = [T3_2].[SalesTerritoryKey])  
89                  GROUP BY [T3_2].[StateProvinceName], [T3_1].[SalesTerritoryGroup]) AS T2_1) AS T1_1</source_statement>  
90        <destination_table>[TEMP_ID_16894]</destination_table>  
91        <shuffle_columns>StateProvinceName;</shuffle_columns>  
92      </dsql_operation>  
93      <dsql_operation operation_type="ON">  
94        <location permanent="false" distribution="AllComputeNodes" />  
95        <sql_operations>  
96          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16893]</sql_operation>  
97        </sql_operations>  
98      </dsql_operation>  
99      <dsql_operation operation_type="RETURN">  
100        <location distribution="AllDistributions" />  
101        <select>SELECT   [T1_1].[col] AS [col],  
102           [T1_1].[col1] AS [col1],  
103           [T1_1].[StateProvinceName] AS [StateProvinceName],  
104           [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
105           [T1_1].[col2] AS [col2]  
106  FROM     (SELECT CONVERT (INT, [T2_1].[col], 0) AS [col],  
107                   CONVERT (INT, [T2_1].[col1], 0) AS [col1],  
108                   [T2_1].[StateProvinceName] AS [StateProvinceName],  
109                   [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
110                   [T2_1].[col] AS [col2]  
111            FROM   (SELECT CASE  
112                            WHEN ([T3_1].[col] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
113                            ELSE ([T3_1].[col1] / CONVERT (MONEY, [T3_1].[col], 0))  
114                           END AS [col],  
115                           CASE  
116                            WHEN ([T3_1].[col2] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
117                            ELSE ([T3_1].[col3] / CONVERT (MONEY, [T3_1].[col2], 0))  
118                           END AS [col1],  
119                           [T3_1].[StateProvinceName] AS [StateProvinceName],  
120                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
121                    FROM   (SELECT ISNULL([T4_1].[col], CONVERT (BIGINT, 0, 0)) AS [col],  
122                                   ISNULL([T4_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col1],  
123                                   ISNULL([T4_1].[col2], CONVERT (BIGINT, 0, 0)) AS [col2],  
124                                   ISNULL([T4_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col3],  
125                                   [T4_1].[StateProvinceName] AS [StateProvinceName],  
126                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
127                            FROM   (SELECT   SUM([T5_1].[col]) AS [col],  
128                                             SUM([T5_1].[col1]) AS [col1],  
129                                             SUM([T5_1].[col2]) AS [col2],  
130                                             SUM([T5_1].[col3]) AS [col3],  
131                                             [T5_1].[StateProvinceName] AS [StateProvinceName],  
132                                             [T5_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
133                                    FROM     [tempdb].[dbo].[TEMP_ID_16894] AS T5_1  
134                                    GROUP BY [T5_1].[StateProvinceName], [T5_1].[SalesTerritoryGroup]) AS T4_1) AS T3_1) AS T2_1) AS T1_1  
135  ORDER BY [T1_1].[col2] DESC</select>  
136      </dsql_operation>  
137      <dsql_operation operation_type="ON">  
138        <location permanent="false" distribution="AllDistributions" />  
139        <sql_operations>  
140          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16894]</sql_operation>  
141        </sql_operations>  
142      </dsql_operation>  
143    </dsql_operations>  
144  </dsql_query>  
  
```  
  
 **Significato dell'output descrizione**  
  
 L'output precedente contiene righe numerate 144. L'output della query possono differire leggermente. L'elenco seguente descrive le sezioni significative.  
  
-   Le righe da 3 a 16 forniscono una descrizione della query in fase di analisi.  
  
-   Riga 17, specifica che il numero totale di operazioni è 9. È possibile trovare l'inizio di ogni operazione, cercando le parole **dsql_operation**.  
  
-   Riga 18 avvia l'operazione 1. Linee 18 e 19 indicano che un **RND_ID** operazione consente di creare un numero di ID casuale che verrà utilizzato per una descrizione dell'oggetto. L'oggetto descritto nell'output precedente è **TEMP_ID_16893**. Il numero sarà diverso.  
  
-   Riga 20 inizia operazione 2. Righe compresi tra 21 e 25: su tutti i nodi di calcolo, creare una tabella temporanea denominata **TEMP_ID_16893**.  
  
-   Riga 26 inizia operazione 3. Righe 27 tramite 37: spostare i dati **TEMP_ID_16893** utilizzando uno spostamento di trasmissione. Viene fornita la query inviata a ogni nodo di calcolo. Riga 37 specifica la tabella di destinazione è **TEMP_ID_16893**.  
  
-   Riga 38 avvia l'operazione di 4. Righe 39 a 40: creare un ID casuale per una tabella. **TEMP_ID_16894** è il numero di ID nell'esempio precedente. Il numero sarà diverso.  
  
-   Riga 41 inizia operazione 5. Righe 42 tramite 46: su tutti i nodi, creare una tabella temporanea denominata **TEMP_ID_16894**.  
  
-   Riga 47 inizia operazione 6. 48 e 91 righe: spostare i dati da diverse tabelle (inclusi **TEMP_ID_16893**) alla tabella **TEMP_ID_16894**, utilizzando una casuale dell'operazione di spostamento. Viene fornita la query inviata a ogni nodo di calcolo. Riga 90 specifica la tabella di destinazione come **TEMP_ID_16894**. Riga 91 specifica le colonne.  
  
-   Riga 92 avvia 7. Righe 93 tramite 97: su tutti i nodi di calcolo, eliminare la tabella temporanea **TEMP_ID_16893**.  
  
-   Riga 98 avvia 8. Righe 99 tramite 135: restituire risultati al client. Usa la query fornita per ottenere i risultati.  
  
-   Riga 136 inizia operazione 9. Le righe dalla 137 alla 140: su tutti i nodi, eliminare la tabella temporanea **TEMP_ID_16894**.  
  
  


