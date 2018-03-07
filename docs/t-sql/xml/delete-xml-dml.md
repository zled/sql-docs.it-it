---
title: eliminare (XML DML) | Documenti Microsoft
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
- XML DML [SQL Server]
- delete keyword
- delete statement [XML DML]
- deleting nodes
ms.assetid: b22c93a4-b84d-4356-af4c-6013322a4b71
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 620eed7dda3887d04cf0d88a01ee5b991025638b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="delete-xml-dml"></a>delete (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Elimina i nodi da un'istanza XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
delete Expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *Espressione*  
 È un'espressione XQuery che identifica i nodi da eliminare. Vengono eliminati tutti i nodi selezionati dall'espressione e i nodi e valori contenuti nei nodi selezionati. Come descritto in [insert (XML DML)](../../t-sql/xml/insert-xml-dml.md), deve essere un riferimento a un nodo esistente nel documento. Non può trattarsi di un nodo costruito. L'espressione non può essere il nodo radice (/). Se l'espressione restituisce una sequenza vuota l'eliminazione non viene eseguita e non vengono restituiti errori.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-deleting-nodes-from-a-document-stored-in-an-untyped-xml-variable"></a>A. Eliminazione di nodi da un documento archiviato in una variabile xml non tipizzata  
 Nell'esempio seguente viene illustrata l'eliminazione di vari nodi da un documento. In primo luogo, un'istanza XML viene assegnata alla variabile di **xml** tipo. Le istruzioni XML DML di eliminazione successive eliminano vari nodi dal documento.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<?Instructions for=TheWC.exe ?>   
<Root>  
 <!-- instructions for the 1st work center -->  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Some text 1  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
SELECT @myDoc  
  
-- delete an attribute  
SET @myDoc.modify('  
  delete /Root/Location/@MachineHours  
')  
SELECT @myDoc  
  
-- delete an element  
SET @myDoc.modify('  
  delete /Root/Location/step[2]  
')  
SELECT @myDoc  
  
-- delete text node (in <Location>  
SET @myDoc.modify('  
  delete /Root/Location/text()  
')  
SELECT @myDoc  
  
-- delete all processing instructions  
SET @myDoc.modify('  
  delete //processing-instruction()  
')  
SELECT @myDoc  
```  
  
### <a name="b-deleting-nodes-from-a-document-stored-in-an-untyped-xml-column"></a>B. Eliminazione di nodi da un documento archiviato in una colonna xml non tipizzata  
 Nell'esempio seguente, un **eliminare** istruzione XML DML rimuove il secondo elemento figlio di <`Features`> dal documento archiviato nella colonna.  
  
```  
CREATE TABLE T (i int, x xml)  
go  
INSERT INTO T VALUES(1,'<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>')  
go  
-- verify the contents before delete  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
-- delete the second feature  
UPDATE T  
SET x.modify('delete /Root/ProductDescription/Features/*[2]')  
-- verify the deletion  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il [Modify () (metodo) (tipo di dati xml)](../../t-sql/xml/modify-method-xml-data-type.md) viene utilizzata per specificare il **eliminare** parola chiave XML DML.  
  
-   Il [query () (metodo) (tipo di dati xml)](../../t-sql/xml/query-method-xml-data-type.md) viene utilizzato per eseguire una query del documento.  
  
### <a name="c-deleting-nodes-from-a-typed-xml-column"></a>C. Eliminazione di nodi da una colonna xml tipizzata  
 In questo esempio elimina i nodi da un documento XML archiviato in istruzioni di produzione tipizzati **xml** colonna.  
  
 Nell'esempio, creare innanzitutto una tabella (T) con un oggetto tipizzato **xml** colonna nel database AdventureWorks. Un'istanza XML di istruzioni di produzione viene quindi copiata dalla colonna Instructions della tabella ProductModel alla tabella T e uno o più nodi vengono eliminati dal documento.  
  
```  
use AdventureWorks  
go  
drop table T  
go  
create table T(ProductModelID int primary key,   
Instructions xml (Production.ManuInstructionsSchemaCollection))  
go  
insert  T   
select ProductModelID, Instructions  
from Production.ProductModel  
where ProductModelID=7  
go  
select Instructions  
from T  
--1) insert <Location 1000/>. Note: <Root> must be singleton in the query  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  insert <MI:Location LocationID="1000"  LaborHours="1000" >  
           These are manu steps at location 1000.   
           <MI:step>New step1 instructions</MI:step>  
           Instructions for step 2 are here  
           <MI:step>New step 2 instructions</MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
  
-- delete an attribute  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/@LaborHours)   
')  
go  
select Instructions  
from T  
-- delete text in <location>  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/text())   
')  
go  
select Instructions  
from T  
-- delete 2nd manu step at location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/MI:step[2])   
')  
go  
select Instructions  
from T  
-- cleanup  
drop table T  
go  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
