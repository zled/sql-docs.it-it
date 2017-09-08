---
title: OPENXML (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENXML_TSQL
- OPENXML
dev_langs:
- TSQL
helpviewer_keywords:
- OPENXML statement
- rowsets [SQL Server], XML documents
- XML [SQL Server], rowset views
ms.assetid: 8088b114-7d01-435a-8e0d-b81abacc86d6
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ff4578d88cdb76468d261843c36043ef4696d92c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="openxml-transact-sql"></a>OPENXML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OpenXML fornisce una vista di un documento XML basata su un set di righe. In quanto provider di set di righe, è possibile utilizzare OPENXML nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] che supportano provider di set di righe quali una tabella, una vista o la funzione OPENROWSET.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OPENXML( idoc int [ in] , rowpattern nvarchar [ in ] , [ flags byte [ in ] ] )   
[ WITH ( SchemaDeclaration | TableName ) ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *IDOC*  
 Handle di documento della rappresentazione interna di un documento XML. La rappresentazione interna di un documento XML viene creata chiamando **sp_xml_preparedocument**.  
  
 *rowpattern*  
 È il modello XPath utilizzato per identificare i nodi (in cui viene passato l'handle nel documento XML di *idoc* parametro) da elaborare come righe.  
  
 *flag*  
 Indica il mapping da utilizzare tra i dati XML e il set di righe relazionale e la modalità di riempimento della colonna spill-over. *flag* è un parametro di input facoltativo e può essere uno dei valori seguenti.  
  
|Valore byte|Description|  
|----------------|-----------------|  
|**0**|Per impostazione predefinita **incentrato sugli attributi** mapping.|  
|**1**|Utilizzare il **incentrato sugli attributi** mapping. Può essere utilizzato in combinazione con XML_ELEMENTS. In questo caso, **incentrato sugli attributi** mapping viene applicato per primo e quindi **incentrato** viene applicato il mapping per tutte le colonne che non sono ancora sottoposte a.|  
|**2**|Utilizzare il **incentrato** mapping. Può essere utilizzato in combinazione con XML_ATTRIBUTES. In questo caso, **incentrato sugli attributi** mapping viene applicato per primo e quindi **incentrato** viene applicato il mapping per tutte le colonne non ancora sottoposte a.|  
|**8**|Può essere utilizzato in combinazione (OR logico) con XML_ATTRIBUTES o XML_ELEMENTS. Nel contesto di recupero, questo flag indica che i dati consumati non devono essere copiati nella proprietà di overflow  **@mp:xmltext** .|  
  
 *SchemaDeclaration*  
 È la definizione dello schema nel formato: *ColName**ColType* [*ColPattern* | *metaproprietà*] [**** *ColNameColType* [*ColPattern* | *metaproprietà*]...]  
  
 *ColName*  
 Nome della colonna nel set di righe.  
  
 *ColType*  
 Tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della colonna nel set di righe. Se i tipi di colonna diversi da sottostante **xml** si verifica il tipo di dati dell'attributo, la coercizione di tipo.  
  
 *Parametro ColPattern*  
 Modello generale XPath facoltativo che indica il criterio di mapping dei nodi XML alle colonne. Se *ColPattern* non viene specificato, il mapping predefinito (**incentrato sugli attributi** o **incentrato** mapping come specificato da *flag* ) viene eseguita.  
  
 Il modello XPath specificato come *ColPattern* viene utilizzata per specificare la natura del mapping (nel caso di **incentrato sugli attributi** e **incentrato** mapping) che sovrascrive o migliora il mapping predefinito indicato in *flag*.  
  
 Il modello XPath generale specificato come *ColPattern* supporta inoltre le metaproprietà.  
  
 *Metaproprietà*  
 Una delle metaproprietà definite da OPENXML. Se *metaproprietà* viene specificato, la colonna contiene le informazioni fornite dalla metaproprietà. Le metaproprietà consentono di estrarre informazioni, ad esempio sulla posizione relativa e sullo spazio dei nomi, relative ai nodi XML. In questo modo viene restituita una quantità di informazioni maggiore rispetto alle informazioni visibili nella rappresentazione testuale.  
  
 *TableName*  
 È il nome della tabella che è possibile assegnare (invece di *SchemaDeclaration*) esiste già una tabella con lo schema desiderato e modelli di colonna non sono richiesti.  
  
## <a name="remarks"></a>Osservazioni  
 La clausola WITH restituisce un formato di set di righe (e le informazioni di mapping aggiuntivi in base alle esigenze) utilizzando uno *SchemaDeclaration* o specificando un valore esistente *TableName*. Se la clausola facoltativa WITH viene omesso, i risultati vengono restituiti un **bordo** formato tabella. Le tabelle edge rappresentano la struttura specifica del documento XML, ad esempio nomi di elementi/attributi, gerarchia del documento, spazi dei nomi, istruzioni di elaborazione e così via, in un'unica tabella.  
  
 Nella tabella seguente descrive la struttura del **bordo** tabella.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**bigint**|ID univoco del nodo del documento.<br /><br /> Il valore dell'ID dell'elemento radice è 0. I valori di ID negativi sono riservati.|  
|**parentid**|**bigint**|Identifica il padre del nodo. Il padre identificato da questo ID non corrisponde necessariamente all'elemento padre. Dipende infatti dal valore NodeType del nodo il cui padre è identificato da questo ID. Se ad esempio il nodo è di tipo testo, il relativo elemento padre potrebbe essere un nodo attributo.<br /><br /> Se il nodo si trova al livello principale nel documento XML, il relativo valore **ParentID** è NULL.|  
|**tipo di nodo**|**int**|Identifica il tipo di nodo. Valore intero corrispondente alla numerazione del tipo di nodo XML DOM.<br /><br /> I possibili tipi di nodo sono i seguenti:<br /><br /> 1 = Nodo elemento<br /><br /> 2 = Nodo attributo<br /><br /> 3 = Nodo testo|  
|**localname**|**nvarchar**|Nome locale dell'elemento o attributo. È NULL se l'oggetto DOM non è associato a un nome.|  
|**prefix**|**nvarchar**|Prefisso dello spazio dei nomi del nome del nodo.|  
|**namespaceuri**|**nvarchar**|URI dello spazio dei nomi del nodo. Se il valore è NULL, non sono presenti spazi dei nomi.|  
|**datatype**|**nvarchar**|Tipo di dati effettivo della riga dell'elemento o attributo. In caso contrario, restituisce NULL. Il tipo di dati viene ricavato dalla DTD o dallo schema inline.|  
|**prev**|**bigint**|ID XML dell'elemento di pari livello precedente. È NULL se non è presente alcun elemento diretto di pari livello precedente.|  
|**text**|**ntext**|Contiene il valore dell'attributo o il contenuto dell'elemento in formato testo (oppure è NULL se il **bordo** voce della tabella non richiede un valore).|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-a-simple-select-statement-with-openxml"></a>A. Utilizzo di un'istruzione SELECT semplice con OPENXML  
 Nell'esempio seguente viene creata una rappresentazione interna dell'immagine XML tramite `sp_xml_preparedocument`. Su tale rappresentazione viene quindi eseguita un'istruzione `SELECT` che utilizza un provider di set di righe `OPENXML`.  
  
 Il *flag* è impostato su `1`. Ciò indica **incentrato sugli attributi** mapping. Sugli attributi XML viene pertanto eseguito il mapping alle colonne del set di righe. Il *rowpattern* specificato come `/ROOT/Customer` identifica il `<Customers>` nodi da elaborare.  
  
 Facoltativo *ColPattern* parametro (modello di colonna) non è specificata perché il nome della colonna corrisponde ai nomi di attributo XML.  
  
 Il provider di set di righe `OPENXML` crea un set di righe composto dalle due colonne `CustomerID` e `ContactName`, da cui vengono ricavate le colonne necessarie, in questo caso tutte le colonne, tramite l'istruzione `SELECT`.  
  
```  
DECLARE @idoc int, @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;  
-- Execute a SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customer',1)  
            WITH (CustomerID  varchar(10),  
                  ContactName varchar(20));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 Se lo stesso `SELECT` viene eseguita un'istruzione *flag* impostato su `2`, che indica **incentrato** mapping, i valori di `CustomerID` e `ContactName` per entrambe le i clienti nel documento XML vengono restituiti come NULL, perché non sono disponibili tutti gli elementi denominati `CustomerID` o `ContactName` nel documento XML.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName  
---------- -----------  
NULL       NULL  
NULL       NULL  
```  
  
### <a name="b-specifying-colpattern-for-mapping-between-columns-and-the-xml-attributes"></a>B. Utilizzo di ColPattern per l'impostazione del mapping tra colonne e attributi XML  
 La query seguente restituisce gli attributi ID cliente, data dell'ordine, ID e quantità dal documento XML. Il *rowpattern* identifica il `<OrderDetails>` elementi. `ProductID` e `Quantity` sono attributi dell'elemento `<OrderDetails>`. Tuttavia, `OrderID`, `CustomerID` e `OrderDate` sono gli attributi dell'elemento padre (`<Orders>`).  
  
 Facoltativo *ColPattern* specificato. a indicare quanto segue:  
  
-   Il `OrderID`, `CustomerID`, e `OrderDate` nella mappa del set di righe agli attributi dell'elemento padre dei nodi identificati da *rowpattern* nel documento XML.  
  
-   Il `ProdID` esegue il mapping di colonna nel set di righe per il `ProductID` attributo e `Qty` esegue il mapping di colonna nel set di righe per il `Quantity` attributi dei nodi identificati *rowpattern*.  
  
 Sebbene il **incentrato** viene specificato un mapping dal *flag* parametro, il mapping specificato in *ColPattern* sovrascrive il mapping.  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">v  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';   
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT stmt using OPENXML rowset provider  
SELECT *  
FROM   OPENXML (@idoc, '/ROOT/Customer/Order/OrderDetail',2)   
         WITH (OrderID       int         '../@OrderID',   
               CustomerID  varchar(10) '../@CustomerID',   
               OrderDate   datetime    '../@OrderDate',   
               ProdID      int         '@ProductID',   
               Qty         int         '@Quantity');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
OrderID CustomerID           OrderDate                 ProdID    Qty  
------------------------------------------------------------------------  
10248      VINET       1996-07-04 00:00:00.000   11      12  
10248      VINET       1996-07-04 00:00:00.000   42      10  
10283      LILAS       1996-08-16 00:00:00.000   72      3  
```  
  
### <a name="c-obtaining-results-in-an-edge-table-format"></a>C. Restituzione di risultati in formato di tabella edge  
 Il documento XML utilizzato nell'esempio seguente è composto dagli elementi `<Customers>`, `<Orders>` e `<Order_0020_Details>`. Prima di tutto, **sp_xml_preparedocument** viene chiamato per ottenere un handle di documento. quindi l'handle di documento viene passato a `OPENXML`.  
  
 Nel `OPENXML` istruzione, il *rowpattern* (`/ROOT/Customers`) identifica i `<Customers>` nodi da elaborare. Poiché la clausola WITH non viene fornita, `OPENXML` restituisce il set di righe in un **bordo** formato tabella.  
  
 Infine il `SELECT` istruzione recupera tutte le colonne di **bordo** tabella.  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customers CustomerID="VINET" ContactName="Paul Henriot">  
   <Orders CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <Order_x0020_Details OrderID="10248" ProductID="11" Quantity="12"/>  
      <Order_x0020_Details OrderID="10248" ProductID="42" Quantity="10"/>  
   </Orders>  
</Customers>  
<Customers CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Orders CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <Order_x0020_Details OrderID="10283" ProductID="72" Quantity="3"/>  
   </Orders>  
</Customers>  
</ROOT>';  
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customers')   
EXEC sp_xml_removedocument @idoc;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esempi d'uso di OPENXML](../../relational-databases/xml/examples-using-openxml.md)  
  
  
