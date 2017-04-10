---
title: "Convertire dati JSON in righe e colonne con la funzione OPENJSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OPENJSON"
  - "JSON, importazione"
  - "importazione JSON"
ms.assetid: 0c139901-01e2-49ef-9d62-57e08e32c68e
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Convertire dati JSON in righe e colonne con la funzione OPENJSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  La funzione dei set di righe **OPENJSON** consente di convertire testo JSON in un set di righe e colonne. È possibile usare **OPENJSON** per eseguire query SQL sulle raccolte JSON o importare testo JSON all'interno di tabelle SQL Server.  
  
> [!NOTE] La funzione **OPENJSON** è disponibile per il **livello di compatibilità 130**. Se il livello di compatibilità del database è inferiore a 130, SQL Server non riuscirà a trovare e a eseguire la funzione **OPENJSON**. Altre funzioni JSON sono disponibili in tutti i livelli di compatibilità. È possibile controllare il livello di compatibilità nella vista sys.databases o nelle proprietà del database.
> 
>   È possibile modificare il livello di compatibilità del database tramite il comando seguente:   
>   ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
  
 La funzione **OPENJSON** riceve un singolo oggetto JSON o una raccolta di oggetti JSON e li trasforma in una o più righe. Per impostazione predefinita, la funzione **OPENJSON** restituisce tutte le coppie chiave:valore presenti nel primo livello dell'oggetto JSON o tutti gli elementi nelle matrici JSON con i relativi indici.  
  
 È possibile specificare lo schema di righe restituito dalla funzione **OPENJSON** tramite la clausola WITH. Questo schema esplicito definisce la struttura dell'output.  
  
## Usare OPENJSON senza lo schema di risultati

In questo esempio semplice la funzione **OPENJSON**  viene usata con lo schema predefinito e restituisce una riga per ogni proprietà dell'oggetto JSON.  
 
Quando si usa la funzione **OPENJSON** senza uno schema specifico per i risultati restituiti, ovvero senza clausola WITH dopo OPENJSON, la funzione restituisce una tabella con tre colonne: nome della proprietà nell'oggetto di input (o indice dell'elemento nella matrice di input), valore della proprietà o dell'elemento della matrice e tipo (ad esempio stringa, numero, valore booleano, matrice o oggetto). Le proprietà dell'oggetto JSON o gli elementi della matrice vengono restituiti in righe distinte.  

-   Per altre info e altri esempi, vedere [Use OPENJSON with the Default Schema &#40;SQL Server&#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md) (Usare OPENJSON con lo schema predefinito (SQL Server)).
-   Per la sintassi e l'utilizzo, vedere [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md). 

```tsql  
SET @json = '{"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}';  
  
SELECT *  
FROM OPENJSON(@json);  
```  
  
**Risultati**  
  
|Key|Valore|tipo|  
|---------|-----------|----------|  
|name|John|1|  
|surname|Doe|1|  
|age|45|2|  
|skills|["SQL","C#","MVC"]|4|
    
## Usare OPENJSON con uno schema esplicito

Ecco un rapido esempio che usa **OPENJSON** con uno schema specificato in modo esplicito.  
  
Quando si specifica lo schema dei risultati restituiti nella clausola WITH della funzione **OPENJSON**, la funzione restituisce una tabella con le colonne definite nella clausola WITH. Nella clausola WITH è possibile specificare colonne di output, i relativi tipi e i percorsi delle proprietà di origine JSON per ogni valore di output. **OPENJSON** esegue l'iterazione attraverso la matrice di oggetti JSON, legge il valore nel percorso specificato per ogni colonna e converte il valore nel tipo specificato.  

-   Per altre info e altri esempi, vedere [Usare OPENJSON con uno schema esplicito &#40;SQL Server&#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md).
-   Per la sintassi e l'utilizzo, vedere [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md).
  
```tsql  
SET @json =   
 N'[  
      {  
        "Order": {  
          "Number":"SO43659",  
          "Date":"2011-05-31T00:00:00"  
        },  
        "AccountNumber":"AW29825",  
        "Item": {  
          "Price":2024.9940,  
          "Quantity":1  
        }  
      },  
      {  
        "Order": {  
          "Number":"SO43661",  
          "Date":"2011-06-01T00:00:00"  
        },  
        "AccountNumber":"AW73565",  
        "Item": {  
          "Price":2024.9940,  
          "Quantity":3  
        }  
     }  
]'  
  
SELECT * FROM  
OPENJSON ( @json )  
WITH (   
             Number   varchar(200) '$.Order.Number' ,  
             Date     datetime     '$.Order.Date',  
             Customer varchar(200) '$.AccountNumber',  
             Quantity int          '$.Item.Quantity'  
)  
```  
  
**Risultati**  
  
|Number|Data|Customer|Quantity|  
|------------|----------|--------------|--------------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|  
|SO43661|2011-06-01T00:00:00|AW73565|3|  
  
 Questa funzione restituisce e formatta gli elementi di una matrice JSON.  
  
-   Per ogni elemento nella matrice JSON la funzione **OPENJSON** genera una nuova riga nella tabella di output. Due elementi nella matrice JSON vengono convertiti in due righe nella tabella restituita.  
  
-   Per ogni colonna specificata tramite la sintassi `colName type json_path` la funzione **OPENJSON** converte il valore trovato negli elementi della matrice nel percorso specificato, li converte nel tipo specificato e popola una cella della tabella di output. In questo esempio i valori per la colonna Date vengono ricavati da ciascun oggetto in un percorso `$.Order.Date` e convertiti in valori datetime.  
  
Dopo che la raccolta JSON è stata trasformata in un set di righe, è possibile eseguire qualsiasi query SQL sui dati restituiti o e questi ultimi in una tabella.  
  
## Altre informazioni sulla funzione OPENJSON e sul supporto JSON predefinito in SQL Server  
 [Post di blog di Jovan Popovic, Microsoft Program Manager](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## Vedere anche  
 [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  