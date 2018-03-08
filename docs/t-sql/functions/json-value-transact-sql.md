---
title: JSON_VALUE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON_VALUE
- JSON_VALUE_TSQL
helpviewer_keywords:
- JSON_VALUE function
- JSON, extracting
- JSON, querying
ms.assetid: cd016e14-11eb-4eaf-bf05-c7cfcc820a10
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: ab4c14769dc51c6d5b97a6ad2fe6f0cb06fad4e0
ms.sourcegitcommit: 19e1c4067142d33e8485cb903a7a9beb7d894015
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2017
---
# <a name="jsonvalue-transact-sql"></a>JSON_VALUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Estrae un valore scalare da una stringa JSON.  
  
 Per estrarre un oggetto o una matrice da una stringa JSON anziché un valore scalare, vedere [JSON_QUERY &#40; Transact-SQL &#41; ](../../t-sql/functions/json-query-transact-sql.md). Per informazioni sulle differenze tra **JSON_VALUE** e **JSON_QUERY**, vedere [confronto tra JSON_VALUE e JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
JSON_VALUE ( expression , path )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Espressione. In genere il nome di una variabile o una colonna che contiene testo JSON.  
 
 Se **JSON_VALUE** trova JSON che non è valido in *espressione* prima di trovare il valore identificato da *percorso*, la funzione restituisce un errore. Se **JSON_VALUE* non viene trovato il valore identificato da *percorso*, analizza l'intero testo e restituisce un errore se rileva JSON che non è valido in un punto qualsiasi in *espressione*.
  
 *percorso*  
 Percorso JSON che specifica la proprietà da estrarre. Per altre informazioni, vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
 
In [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], è possibile specificare una variabile come valore di *percorso*.
  
 Se il formato di *percorso* non è valido, **JSON_VALUE** restituisce un errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore di testo di tipo nvarchar (4000). Le regole di confronto del valore restituito è lo stesso come le regole di confronto dell'espressione di input.  
  
 Se il valore è maggiore di 4000 caratteri:  
  
-   In modalità lax, **JSON_VALUE** restituisce null.  
  
-   In modalità strict **JSON_VALUE** restituisce un errore.  
  
 Se è necessario restituire valori scalari maggiore di 4000 caratteri, utilizzare **OPENJSON** anziché **JSON_VALUE**. Per altre informazioni, vedere [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni

### <a name="lax-mode-and-strict-mode"></a>Modalità LAX e la modalità strict

 Si consideri il testo JSON seguente:  
  
```json  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }'  
```  
  
 Nella tabella seguente viene confrontato il comportamento di **JSON_VALUE** in modalità lax e in modalità strict. Per ulteriori informazioni sulla specifica la modalità percorso facoltativo (lax o strict), vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Percorso|Valore restituito in modalità lax|Valore restituito in modalità strict|Altre informazioni|  
|----------|------------------------------|---------------------------------|---------------|  
|$|NULL|Errore|Non è un valore scalare.<br /><br /> Utilizzare **JSON_QUERY** invece.|  
|$. info.type|N '1'|N '1'|N/a|  
|$. info.address.town|N'Bristol'|N'Bristol'|N/a|  
|$. Info." indirizzo"|NULL|Errore|Non è un valore scalare.<br /><br /> Utilizzare **JSON_QUERY** invece.|  
|$. info.tags|NULL|Errore|Non è un valore scalare.<br /><br /> Utilizzare **JSON_QUERY** invece.|  
|$. info.type[0]|NULL|Errore|Non è una matrice.|  
|$. info.none|NULL|Errore|Proprietà non esiste.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="example-1"></a>Esempio 1  
 L'esempio seguente usa i valori delle proprietà JSON `town` e `state` nei risultati della query. Poiché **JSON_VALUE** mantiene le regole di confronto dell'origine, l'ordinamento dei risultati dipende dalle regole di confronto del `jsonInfo` colonna. 

> [!NOTE]
> (In questo esempio si presuppone che una tabella denominata `Person.Person` contiene un `jsonInfo` colonna di testo JSON e che questa colonna contiene la struttura illustrata in precedenza nella spiegazione della modalità lax e la modalità strict. Nel database di esempio AdventureWorks, il `Person` tabella non contiene infatti un `jsonInfo` colonna.)
  
```sql  
SELECT FirstName, LastName,
 JSON_VALUE(jsonInfo,'$.info.address[0].town') AS Town
FROM Person.Person
WHERE JSON_VALUE(jsonInfo,'$.info.address[0].state') LIKE 'US%'
ORDER BY JSON_VALUE(jsonInfo,'$.info.address[0].town')
```  
  
### <a name="example-2"></a>Esempio 2  
 Nell'esempio seguente estrae il valore della proprietà JSON `town` in una variabile locale.  
  
```sql  
DECLARE @jsonInfo NVARCHAR(MAX)
DECLARE @town NVARCHAR(32)

SET @jsonInfo=N'<array of address info>'

SET @town=JSON_VALUE(@jsonInfo,'$.info.address.town')
```  
  
### <a name="example-3"></a>Esempio 3  
 L'esempio seguente crea le colonne calcolate in base ai valori delle proprietà JSON.  
  
```sql  
CREATE TABLE dbo.Store
 (
  StoreID INT IDENTITY(1,1) NOT NULL,
  Address VARCHAR(500),
  jsonContent NVARCHAR(8000),
  Longitude AS JSON_VALUE(jsonContent, '$.address[0].longitude'),
  Latitude AS JSON_VALUE(jsonContent, '$.address[0].latitude')
 )
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di percorso JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [I dati JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
