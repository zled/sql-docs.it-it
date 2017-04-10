---
title: "Uso dei tipi di dati di R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Uso dei tipi di dati di R
  Mentre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta diversi tipi di decine dati, R è un numero limitato di tipi di dati scalari (numerici, integer, caratteri complessi, logici, data/ora e non elaborati). Pertanto, quando si usano dati da  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] negli script R, possono verificarsi varie situazioni:  
  
-   I dati vengono convertiti in modo implicito in un tipo di dati compatibile.  
  
-   I dati non possono essere convertiti in modo implicito e viene restituito un errore.  
  
 In genere, ogni volta che si hanno dubbi sull'uso di una particolare struttura di dati o di un tipo di dati specifico in R, usare la funzione  `str()` per ottenere la struttura interna e il tipo dell'oggetto R. Il risultato della funzione viene stampato nella console R ed è disponibile anche nei risultati della query, nella scheda **Messaggi** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Se una particolare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati non è supportato da R, ma è necessario utilizzare le colonne di dati nello script R, è consigliabile utilizzare il [CAST e CONVERT & #40; Transact-SQL & #41;](../../t-sql/functions/cast-and-convert-transact-sql.md) funzioni per garantire che il tipo di dati le conversioni vengono eseguite come previsto prima di utilizzare i dati nello script R.  
  
 Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati, vedere [tipi di dati e 40 #; Transact-SQL & #41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
## Conversione del tipo di dati tra R e SQL Server  
 La tabella seguente mostra le modifiche del tipo di dati e dei valori quando i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono usati in uno script R e quindi restituiti a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|||||  
|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tipo|Classe R|Tipo in **RESULT SET**|Commenti|  
|**smalldatetime**|`POSIXct`|**datetime**|Rappresentato come GMT|  
|**smallmoney**|`numeric`|**float**||  
|**datetime**|`POSIXct`|**datetime**|Rappresentato come GMT|  
|**money**|`numeric`|**float**||  
|**uniqueidentifier**|`character`|**varchar(max)**||  
|**Numeric(p,s)**|`numeric`|**float**||  
|**Decimal(p,s)**|`numeric`|**float**||  
|**data**|`POSIXct`|**datetime**|Rappresentato come GMT|  
|**tinyint**|`integer`|**int**||  
|**bit**|`logical`|**bit**||  
|**smallint**|`integer`|**int**||  
|**int**|`integer`|**int**||  
|**float**|`numeric`|**float**||  
|**real**|`numeric`|**float**||  
|**bigint**|`numeric`|**float**||  
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Consentito solo come parametro di input e di output|  
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary (n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Consentito solo come parametro di input e di output|  
|**varchar (n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(max)**|`raw`|**varbinary(max)**|Consentito solo come parametro di input e di output|  
  
## Esempi di conversione del tipo di dati  
 La query seguente ottiene una serie di valori da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella e utilizza la stored procedure  [sp_execute_external_script & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per restituire i valori mediante il runtime di R.  
  
```  
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```  
  
 **Risultati**  
  
||||||  
|-|-|-|-|-|  
||C1|C2|C3|C4|  
|1|1|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|  
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|  
  
 Si noti l'uso della funzione `str` in R per ottenere lo schema di dati di output. Questa funzione restituisce le informazioni seguenti:  
  
```  
'data.frame':2 obs. of  4 variables:   
 $ c1: int  1 -11   
 $ c2: Factor w/ 2 levels "Hello","world": 1 2   
 $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1   
 $ cR: num  4 2  
```  
  
 È possibile vedere che le conversioni del tipo di dati seguenti sono state eseguite in modo implicito come parte di questa query:  
  
-   **Colonna C1**. La colonna è rappresentata come **int** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `integer` in R, e **int** nel set di risultati di output.  
  
     Non è stata eseguita alcuna conversione del tipo di dati.  
  
-   **Colonna C2**. La colonna è rappresentata come **varchar (10)** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `factor` in R, e **varchar (max)** nell'output.  
  
     Si noti come l'output cambia; qualsiasi stringa da R (un fattore o una stringa normale) sarà rappresentato come **varchar (max)**, indipendentemente dalla lunghezza delle stringhe.  
  
-   **Colonna C3**.  La colonna è rappresentata come **uniqueidentifier** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `character` in R, e **varchar (max)** nell'output.  
  
     Si noti la conversione del tipo di dati. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta il **uniqueidentifier** ma non R; pertanto, gli identificatori sono rappresentati come stringhe.  
  
-   **Colonna C4**. La colonna contiene valori generati dallo script R e non presenti nei dati originali.  
 
 ## Vedere anche
 [Caratteristiche e attività di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)
  
  