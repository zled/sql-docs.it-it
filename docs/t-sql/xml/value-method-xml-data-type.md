---
title: Value () (metodo) (tipo di dati xml) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- value method
- value() method
ms.assetid: 298a7361-dc9a-4902-9b1e-49a093cd831d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7a3822e0469836b59369eb676ece956533d4df58
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="value-method-xml-data-type"></a>Metodo value() (tipo di dati xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esegue un'espressione XQuery sul codice XML e restituisce un valore di tipo SQL, rappresentato da un valore scalare.  
  
 È in genere utilizzare questo metodo per estrarre un valore da un'istanza XML archiviata in un **xml** tipo colonna, parametro o variabile. Ciò consente di specificare query SELECT che combinano o confrontano dati XML con dati di colonne non di tipo XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
value (XQuery, SQLType)  
```  
  
## <a name="arguments"></a>Argomenti  
 *XQuery*  
 È il *XQuery* espressione, una valore letterale stringa, che recupera i dati all'interno dell'istanza XML. Deve restituire almeno un valore, In caso contrario, viene restituito un errore.  
  
 *SQLType*  
 Tipo SQL preferito che verrà restituito, rappresentato da un valore letterale stringa. Il tipo restituito di questo metodo corrisponde la *SQLType* parametro. *SQLType* non può essere un **xml** tipo di dati, un tipo common language runtime (CLR) definito dall'utente, **immagine**, **testo**, **ntext**, o **sql_variant** tipo di dati. *SQLType* può essere SQL, tipo di dati definito dall'utente.  
  
 Il **Value ()** metodo utilizza il [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERTIRE operatore in modo implicito e tenta di convertire il risultato dell'espressione XQuery, la rappresentazione di stringa serializzata, dal tipo XSD al tipo SQL corrispondente specificato dal [!INCLUDE[tsql](../../includes/tsql-md.md)] conversione. Per ulteriori informazioni sulle regole di cast di tipo per CONVERT, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
> [!NOTE]  
>  Per motivi di prestazioni, anziché utilizzare il **Value ()** metodo in un predicato da confrontare con un valore relazionale, utilizzare **exist ()** con **SQL: Column**. Questa operazione è illustrata nell'esempio D seguente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-the-value-method-against-an-xml-type-variable"></a>A. Utilizzo del metodo value() su una variabile di tipo xml  
 Nell'esempio seguente, un'istanza XML viene archiviata in una variabile di tipo `xml`. Il metodo `value()` recupera il valore dell'attributo `ProductID` dal codice XML e quindi lo assegna a una variabile `int`.  
  
```  
DECLARE @myDoc xml  
DECLARE @ProdID int  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
  
SET @ProdID =  @myDoc.value('(/Root/ProductDescription/@ProductID)[1]', 'int' )  
SELECT @ProdID  
```  
  
 Il risultato restituito è il valore 1.  
  
 Benché nell'istanza XML sia presente un solo attributo `ProductID`, in base alle regole della tipizzazione statica è necessario specificare in modo esplicito che l'espressione di percorso restituisce un singleton. Alla fine dell'espressione di percorso viene pertanto specificato `[1]`. Per ulteriori informazioni sulla tipizzazione statica, vedere [XQuery e tipizzazione statica](../../xquery/xquery-and-static-typing.md).  
  
### <a name="b-using-the-value-method-to-retrieve-a-value-from-an-xml-type-column"></a>B. Utilizzo del metodo value() per recuperare un valore da una colonna di tipo xml  
 La query seguente viene eseguita un' **xml** colonna di tipo (`CatalogDescription`) nei `AdventureWorks` database. La query recupera i valori dell'attributo `ProductModelID` da ognuna delle istanze XML archiviate nella colonna.  
  
```  
SELECT CatalogDescription.value('             
    declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";             
       (/PD:ProductDescription/@ProductModelID)[1]', 'int') AS Result             
FROM Production.ProductModel             
WHERE CatalogDescription IS NOT NULL             
ORDER BY Result desc             
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Viene utilizzata la parola chiave `namespace` per definire un prefisso dello spazio dei nomi.  
  
-   In base ai requisiti per la tipizzazione statica, nel metodo `[1]` viene aggiunto `value()` alla fine dell'espressione di percorso, allo scopo di indicare in modo esplicito che l'espressione restituisce un singleton.  
  
 Risultato parziale:  
  
```  
-----------  
35           
34           
...  
```  
  
### <a name="c-using-the-value-and-exist-methods-to-retrieve-values-from-an-xml-type-column"></a>C. Utilizzo dei metodi value() ed exist() per recuperare valori da una colonna di tipo xml  
 Nell'esempio seguente viene illustrato l'utilizzo di `value()` (metodo) e [metodo exist ()](../../t-sql/xml/exist-method-xml-data-type.md) del **xml** tipo di dati. Il metodo `value()` consente di recuperare i valori dell'attributo `ProductModelID` dal codice XML. Il metodo `exist()` nella clausola `WHERE` consente di filtrare le righe della tabella.  
  
 La query recupera dalle istanze XML gli ID dei modelli del prodotto che includono tra le funzionalità informazioni relative alla garanzia (elemento <`Warranty`>). La condizione della clausola `WHERE` utilizza il metodo `exist()` per recuperare solo le righe che soddisfano tale condizione.  
  
```  
SELECT CatalogDescription.value('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           (/PD:ProductDescription/@ProductModelID)[1] ', 'int') as Result  
FROM  Production.ProductModel  
WHERE CatalogDescription.exist('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   La colonna `CatalogDescription` è una colonna XML tipizzata, ovvero a tale colonna è associato una raccolta di schemi. Nel [prologo XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), la dichiarazione dello spazio dei nomi viene utilizzata per definire il prefisso utilizzato successivamente nel corpo della query.  
  
-   Se il metodo `exist()` restituisce `1` (True), significa che l'istanza XML include l'elemento figlio <`Warranty`> come una delle funzionalità.  
  
-   Il metodo `value()` della clausola `SELECT` recupera quindi i valori dell'attributo `ProductModelID` come valori interi.  
  
 Risultato parziale:  
  
```  
Result       
-----------  
19           
23           
...  
```  
  
### <a name="d-using-the-exist-method-instead-of-the-value-method"></a>D. Utilizzo del metodo exist() in sostituzione del metodo value()  
 Per motivi relativi alle prestazioni, anziché utilizzare il metodo `value()` in un predicato per eseguire il confronto con un valore relazionale, è consigliabile utilizzare `exist()` con `sql:column()`. Esempio:  
  
```  
CREATE TABLE T (c1 int, c2 varchar(10), c3 xml)  
GO  
  
SELECT c1, c2, c3   
FROM T  
WHERE c3.value( '/root[1]/@a', 'integer') = c1  
GO  
```  
  
 È possibile scrivere il codice nel modo seguente:  
  
```  
SELECT c1, c2, c3   
FROM T  
WHERE c3.exist( '/root[@a=sql:column("c1")]') = 1  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
