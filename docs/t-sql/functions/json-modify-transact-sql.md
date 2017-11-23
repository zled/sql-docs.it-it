---
title: JSON_MODIFY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 96bc8255-a037-4907-aec4-1a9c30814651
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0c4f5c0f65e6f7ae8b532cb42d117fa49fc83b00
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="jsonmodify-transact-sql"></a>JSON_MODIFY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Aggiorna il valore di una proprietà in una stringa JSON e restituisce la stringa JSON aggiornata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
JSON_MODIFY ( expression , path , newValue )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Espressione. In genere il nome di una variabile o una colonna che contiene testo JSON.  
  
 **JSON_MODIFY** restituisce un errore se *espressione* non contiene JSON valido.  
  
 *percorso*  
 Un'espressione di percorso JSON che specifica la proprietà da aggiornare.

 *percorso* presenta la seguente sintassi:  
  
 `[append] [ lax | strict ] $.<json path>`  
  
-   *aggiungere*  
    Modificatore facoltativo che specifica che deve essere aggiunto il nuovo valore nella matrice a cui fa riferimento  *\<percorso json >*.  
  
-   *LAX*  
    Specifica che la proprietà a cui fa riferimento  *\<percorso json >* non deve esistere. Se la proprietà non è presente, JSON_MODIFY tenta di inserire il nuovo valore nel percorso specificato. Inserimento potrebbe non riuscire se la proprietà non può essere inserita nel percorso. Se non si specifica *lax* o *strict*, *lax* è la modalità predefinita.  
  
-   *Strict*  
    Specifica che la proprietà a cui fa riferimento  *\<percorso json >* deve essere nell'espressione di JSON. Se la proprietà non è presente, JSON_MODIFY restituisce un errore.  
  
-   *\<percorso JSON >*  
    Specifica il percorso per la proprietà da aggiornare. Per altre informazioni, vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
In [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], è possibile specificare una variabile come valore di *percorso*.

**JSON_MODIFY** restituisce un errore se il formato di *percorso* non è valido.  
  
 *newValue*  
 Il nuovo valore per la proprietà specificata da *percorso*.  
  
 In modalità lax JSON_MODIFY Elimina la chiave specificata, se il nuovo valore è NULL.  
  
Se il tipo del valore è NVARCHAR o VARCHAR, JSON_MODIFY ignora tutti i caratteri speciali nel nuovo valore. Un valore di testo non sottoposto a escape se correttamente formattati JSON generato da FOR JSON, JSON_QUERY o JSON_MODIFY.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il valore aggiornato del *espressione* come correttamente formattato il testo JSON.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione JSON_MODIFY consente di aggiornare il valore di una proprietà esistente, inserire una nuova coppia chiave-valore o eliminare una chiave in base a una combinazione di modalità e valori forniti.  
  
 Nella tabella seguente viene confrontato il comportamento di **JSON_MODIFY** in modalità lax e in modalità strict. Per ulteriori informazioni sulla specifica la modalità percorso facoltativo (lax o strict), vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Valore esistente|Esiste un percorso|Modalità LAX|Modalità Strict|  
|--------------------|-----------------|--------------|-----------------|  
|Non è NULL|Sì|Aggiornare il valore esistente.|Aggiornare il valore esistente.|  
|Non è NULL|No|Provare a creare una nuova coppia chiave-valore nel percorso specificato.<br /><br /> Questo potrebbe non riuscire. Ad esempio, se si specifica il percorso `$.user.setting.theme`, JSON_MODIFY non inserisce la chiave `theme` se il `$.user` o `$.user.settings` oggetti non esistono, o se le impostazioni di una matrice o un valore scalare.|Errore: INVALID_PROPERTY|  
|NULL|Sì|Eliminare la proprietà esistente.|Impostare il valore esistente su null.|  
|NULL|No|Nessuna azione. Il primo argomento viene restituito come risultato.|Errore: INVALID_PROPERTY|  
  
 In modalità lax JSON_MODIFY tenta di creare una nuova coppia chiave-valore, ma in alcuni casi potrebbe verificarsi un errore.  
  
## <a name="examples"></a>Esempi  
  
### <a name="example---basic-operations"></a>Esempio: operazioni di base  
 L'esempio seguente mostra le operazioni di base che possono essere eseguite con testo JSON.  
  
 **Query**  
  
```sql  

DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update name  

SET @info=JSON_MODIFY(@info,'$.name','Mike')

PRINT @info

-- Insert surname  

SET @info=JSON_MODIFY(@info,'$.surname','Smith')

PRINT @info

-- Delete name  

SET @info=JSON_MODIFY(@info,'$.name',NULL)

PRINT @info

-- Add skill  

SET @info=JSON_MODIFY(@info,'append $.skills','Azure')

PRINT @info
```  
  
 **Risultati**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---multiple-updates"></a>Esempio: più aggiornamenti  
 È possibile aggiornare solo una proprietà con JSON_MODIFY. Se è necessario eseguire più aggiornamenti, è possibile utilizzare più chiamate JSON_MODIFY.  
  
 **Query**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Multiple updates  

SET @info=JSON_MODIFY(JSON_MODIFY(JSON_MODIFY(@info,'$.name','Mike'),'$.surname','Smith'),'append $.skills','Azure')

PRINT @info
```  
  
 **Risultati**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---rename-a-key"></a>Esempio: ridenominazione di una chiave  
 Nell'esempio seguente viene illustrato come rinominare una proprietà in testo JSON con la funzione JSON_MODIFY. Innanzitutto è possibile accettare il valore di una proprietà esistente e inserirlo come una nuova coppia chiave-valore. È quindi possibile eliminare la chiave precedente impostando il valore della proprietà precedente su NULL.  
  
 **Query**  
  
```sql  
DECLARE @product NVARCHAR(100)='{"price":49.99}'

PRINT @product

-- Rename property  

SET @product=
 JSON_MODIFY(
  JSON_MODIFY(@product,'$.Price',CAST(JSON_VALUE(@product,'$.price') AS NUMERIC(4,2))),
  '$.price',
  NULL
 )

PRINT @product
```  
  
 **Risultati**  
  
```json  
{
    "price": 49.99
} {
    "Price": 49.99
}
```  
  
 Se si non esegue il cast il nuovo valore a un tipo numerico, JSON_MODIFY lo considera come testo e racchiude tra virgolette doppie.  
  
### <a name="example---increment-a-value"></a>Esempio: un valore di incremento  
 Nell'esempio seguente viene illustrato come incrementare il valore di una proprietà in testo JSON con la funzione JSON_MODIFY. Innanzitutto è possibile accettare il valore della proprietà esistente e inserirlo come una nuova coppia chiave-valore. È quindi possibile eliminare la chiave precedente impostando il valore della proprietà precedente su NULL.  
  
 **Query**  
  
```sql  
DECLARE @stats NVARCHAR(100)='{"click_count": 173}'

PRINT @stats

-- Increment value  

SET @stats=JSON_MODIFY(@stats,'$.click_count',
 CAST(JSON_VALUE(@stats,'$.click_count') AS INT)+1)

PRINT @stats
```  
  
 **Risultati**  
  
```json  
{
    "click_count": 173
} {
    "click_count": 174
}
```  
  
### <a name="example---modify-a-json-object"></a>Esempio: modificare un oggetto JSON  
 JSON_MODIFY considera il *newValue* argomento come testo normale anche se contiene correttamente formattato il testo JSON. Di conseguenza, l'output JSON della funzione è racchiuso tra virgolette doppie e tutti i caratteri speciali sono caratteri di escape, come illustrato nell'esempio seguente.  
  
 **Query**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array

SET @info=JSON_MODIFY(@info,'$.skills','["C#","T-SQL","Azure"]')

PRINT @info
```  
  
 **Risultati**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": "["C#","T-SQL","Azure"]"
}
```  
  
 Per evitare la sequenza di escape automatica, specificare *newValue* utilizzando la funzione JSON_QUERY. JSON_MODIFY sa che il valore restituito da JSON_MODIFY sia correttamente formattato JSON, in modo che non di escape il valore.  
  
 **Query**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array  

SET @info=JSON_MODIFY(@info,'$.skills',JSON_QUERY('["C#","T-SQL","Azure"]'))

PRINT @info
```  
  
 **Risultati**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": ["C#", "T-SQL", "Azure"]
}
```  
  
### <a name="example---update-a-json-column"></a>Esempio: aggiornamento di una colonna JSON  
 Nell'esempio seguente aggiorna il valore di una proprietà in una colonna di tabella che contiene JSON.  
  
```sql  
UPDATE Employee
SET jsonCol=JSON_MODIFY(jsonCol,"$.info.address.town",'London')
WHERE EmployeeID=17
 
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di percorso JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [I dati JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
