---
title: JSON_QUERY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/02/2016
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
- JSON_QUERY
- JSON_QUERY_TSQL
helpviewer_keywords:
- JSON, extracting
- JSON, querying
- JSON_QUERY function
ms.assetid: 1ab0d90f-19b6-4988-ab4f-22fdf28b7c79
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 310d85e26226cd54eff5d1c99e94b235348a90f7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="jsonquery-transact-sql"></a>JSON_QUERY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Estrae un oggetto o una matrice da una stringa JSON.  
  
 Per estrarre un valore scalare da una stringa JSON anziché un oggetto o una matrice, vedere [JSON_VALUE &#40; Transact-SQL &#41; ](../../t-sql/functions/json-value-transact-sql.md). Per informazioni sulle differenze tra **JSON_VALUE** e **JSON_QUERY**, vedere [confronto tra JSON_VALUE e JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
JSON_QUERY ( expression [ , path ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Espressione. In genere il nome di una variabile o una colonna che contiene testo JSON.  
  
 Se **JSON_QUERY** trova JSON che non è valido in *espressione* prima di trovare il valore identificato da *percorso*, la funzione restituisce un errore. Se **JSON_QUERY** non viene trovato il valore identificato da *percorso*, analizza l'intero testo e restituisce un errore se rileva JSON che non è valido in un punto qualsiasi in *espressione*.  
  
 *percorso*  
 Percorso JSON che specifica l'oggetto o matrice da estrarre.

In [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], è possibile specificare una variabile come valore di *percorso*.

Il percorso JSON è possibile specificare la modalità lax o strict per l'analisi. Se non si specifica la modalità di analisi, lax è la modalità predefinita. Per altre informazioni, vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  

Il valore predefinito per *percorso* è '$'. Di conseguenza, se non si fornisce un valore per *percorso*, **JSON_QUERY** restituisce l'input *espressione*.

Se il formato di *percorso* non è valido, **JSON_QUERY** restituisce un errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un frammento JSON di tipo nvarchar (max). Le regole di confronto del valore restituito è lo stesso come le regole di confronto dell'espressione di input.  
  
 Se il valore non è un oggetto o una matrice:  
  
-   In modalità lax, **JSON_QUERY** restituisce null.  
  
-   In modalità strict **JSON_QUERY** restituisce un errore.  
  
## <a name="remarks"></a>Osservazioni  

### <a name="lax-mode-and-strict-mode"></a>Modalità LAX e la modalità strict

 Si consideri il testo JSON seguente:  
  
```json  
{
    "info": {
        "type": 1,
        "address": {
            "town": "Bristol",
            "county": "Avon",
            "country": "England"
        },
        "tags": ["Sport", "Water polo"]
    },
    "type": "Basic"
} 
```  
  
 Nella tabella seguente viene confrontato il comportamento di **JSON_QUERY** in modalità lax e in modalità strict. Per ulteriori informazioni sulla specifica la modalità percorso facoltativo (lax o strict), vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Percorso|Valore restituito in modalità lax|Valore restituito in modalità strict|Altre informazioni|  
|----------|------------------------------|---------------------------------|---------------|  
|$|Restituisce l'intero testo JSON.|Restituisce l'intero testo JSON.|N/a|  
|$. info.type|NULL|Errore|Non è un oggetto o matrice.<br /><br /> Utilizzare **JSON_VALUE** invece.|  
|$. info.address.town|NULL|Errore|Non è un oggetto o matrice.<br /><br /> Utilizzare **JSON_VALUE** invece.|  
|$. Info." indirizzo"|N'{"città": "Bristol", "regione": "Avon", "paese": "Inghilterra"} "|N'{"città": "Bristol", "regione": "Avon", "paese": "Inghilterra"} "|N/a|  
|$. info.tags|N '["Sport", "Acqua sagoma"]'|N '["Sport", "Acqua sagoma"]'|N/a|  
|$. info.type[0]|NULL|Errore|Non è una matrice.|  
|$. info.none|NULL|Errore|Proprietà non esiste.|  

### <a name="using-jsonquery-with-for-json"></a>Utilizzo di JSON_QUERY con FOR JSON

**JSON_QUERY** restituisce un frammento JSON valido. Di conseguenza, **FOR JSON** non caratteri di escape speciali nel **JSON_QUERY** valore restituito.

Se si restituisce risultati con FOR JSON e includere dati che sono già in formato JSON (in una colonna o come risultato di un'espressione), eseguire il wrapping di dati JSON con **JSON_QUERY** senza il *percorso* parametro.

## <a name="examples"></a>Esempi  
  
### <a name="example-1"></a>Esempio 1  
 Nell'esempio seguente viene illustrato come restituire un frammento JSON da un `CustomFields` colonna nei risultati della query.  
  
```sql  
SELECT PersonID,FullName,
 JSON_QUERY(CustomFields,'$.OtherLanguages') AS Languages
FROM Application.People
```  
  
### <a name="example-2"></a>Esempio 2  
Nell'esempio seguente viene illustrato come includere frammenti JSON nell'output della clausola FOR JSON.  
  
```sql  
SELECT StockItemID, StockItemName,
         JSON_QUERY(Tags) as Tags,
         JSON_QUERY(CONCAT('["',ValidFrom,'","',ValidTo,'"]')) ValidityPeriod
FROM Warehouse.StockItems
FOR JSON PATH
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di percorso JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [I dati JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
