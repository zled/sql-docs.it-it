---
title: Sostituire il valore di (XML DML) | Documenti Microsoft
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
- update keyword
- replacement values [XML DML]
- updating node values
- replace value of XML DML statement
ms.assetid: c310f6df-7adf-493b-b56b-8e3143b13ae7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 236e919d1817e100c043e29de94c25442aac776f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="replace-value-of-xml-dml"></a>replace value of (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Aggiorna il valore di un nodo nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
replace value of Expression1   
with Expression2  
```  
  
## <a name="arguments"></a>Argomenti  
 *Expression1*  
 Identifica un nodo di cui è necessario aggiornare il valore. Deve identificare solo un singolo nodo, Vale a dire *Expression1* deve essere un singleton statico. Se l'istanza XML è tipizzata, il nodo deve essere di tipo semplice. Nel caso in cui vengano selezionati più nodi, viene restituito un errore. Se *Expression1* restituisce una sequenza vuota, alcuna sostituzione di valori viene eseguita e non vengono restituiti errori. *Expression1* deve restituire un singolo elemento con tipizzazione semplice contenuto (tipo elenco o atomico), un nodo di testo o un nodo attributo. *Expression1* non può essere un tipo di unione, un tipo complesso, un'istruzione di elaborazione, un nodo di documento o un nodo di commento. In caso contrario, viene restituito un errore.  
  
 *Expression2*  
 Identifica il nuovo valore del nodo. Questo può essere un'espressione che restituisce un nodo con tipizzazione semplice, perché **data ()** verrà utilizzato in modo implicito. Se il valore è un elenco di valori, il **aggiornare** istruzione sostituisce il valore precedente con l'elenco. In caso di modifica di un'istanza XML tipizzata, *Expression2* deve essere dello stesso tipo o un sottotipo di *espressione*1. In caso contrario, viene restituito un errore. In caso di modifica di un'istanza XML non tipizzata, *Expression2* deve essere un'espressione che è possibile atomizzare. In caso contrario, viene restituito un errore.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti del **sostituire il valore di** istruzione XML DML viene illustrato come aggiornare i nodi in un documento XML.  
  
### <a name="a-replacing-values-in-an-xml-instance"></a>A. Sostituzione di valori in un'istanza XML  
 Nell'esempio seguente, un'istanza del documento viene innanzitutto assegnata a una variabile di **xml** tipo. Quindi, **sostituire il valore di** istruzioni XML DML aggiornare i valori nel documento.  
  
```  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Manufacturing steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>';  
SELECT @myDoc;  
  
-- update text in the first manufacturing step  
SET @myDoc.modify('  
  replace value of (/Root/Location/step[1]/text())[1]  
  with     "new text describing the manu step"  
');  
SELECT @myDoc;  
-- update attribute value  
SET @myDoc.modify('  
  replace value of (/Root/Location/@LaborHours)[1]  
  with     "100.0"  
');  
SELECT @myDoc;  
```  
  
 Si noti che la destinazione da aggiornare deve essere al massimo un singolo nodo specificato in modo esplicito nell'espressione di percorso aggiungendo "[1]" alla fine dell'espressione.  
  
### <a name="b-using-the-if-expression-to-determine-replacement-value"></a>B. Utilizzo dell'espressione if per determinare il valore di sostituzione  
 È possibile specificare il **se** in expression2 all'interno dell'espressione di **sostituire il valore di XML DML** istruzione, come illustrato nell'esempio seguente. Expression1 indica che l'attributo LaborHours del primo centro di lavorazione deve essere aggiornato. Expression2 utilizza un **se** espressione per determinare il nuovo valore dell'attributo LaborHours.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours=".1"  
            MachineHours=".2" >Manu steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
--SELECT @myDoc  
  
SET @myDoc.modify('  
  replace value of (/Root/Location[1]/@LaborHours)[1]  
  with (  
       if (count(/Root/Location[1]/step) > 3) then  
         "3.0"  
       else  
          "1.0"  
      )  
')  
SELECT @myDoc  
```  
  
### <a name="c-updating-xml-stored-in-an-untyped-xml-column"></a>C. Aggiornamento di un'istanza XML archiviata in una colonna XML non tipizzata  
 Nell'esempio seguente viene aggiornata un'istanza XML archiviata in una colonna:  
  
```  
drop table T  
go  
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
-- verify the current <ProductDescription> element  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
-- update the ProductName attribute value  
UPDATE T  
SET x.modify('  
  replace value of (/Root/ProductDescription/@ProductName)[1]  
  with "New Road Bike" ')  
-- verify the update  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
```  
  
### <a name="d-updating-xml-stored-in-a-typed-xml-column"></a>D. Aggiornamento di un'istanza XML archiviata in una colonna XML tipizzata  
 In questo esempio, vengono sostituiti i valori di un documento di istruzioni di produzione archiviato in una colonna XML tipizzata.  
  
 Innanzitutto, viene creata una tabella (T) con una colonna XML tipizzata nel database AdventureWorks. Un'istanza del codice XML delle istruzioni di produzione viene quindi copiata dalla colonna Instructions della tabella ProductModel nella tabella T. Gli inserimenti vengono quindi applicati al codice XML nella tabella T.  
  
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
--insert a new location - <Location 1000/>.   
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
insert <MI:Location LocationID="1000"  LaborHours="1000"  LotSize="1000" >  
           <MI:step>Do something using <MI:tool>hammer</MI:tool></MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
go  
-- Now replace manu. tool in location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/MI:step/MI:tool)[1]   
  with   "screwdriver"  
')  
go  
select Instructions  
from T  
-- Now replace value of lot size  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/@LotSize)[1]   
  with   500 cast as xs:decimal ?  
')  
go  
select Instructions  
from T  
```  
  
 Si noti l'uso di **cast** durante la sostituzione del valore LotSize. necessario quando il valore deve essere di un tipo specifico. In questo esempio, se il valore è 500, non è necessario eseguire il cast esplicito.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
