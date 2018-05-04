---
title: Expanded-QName (XQuery) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- expanded-QName function
- fn:expanded-QName function
ms.assetid: b8377042-95cc-467b-9ada-fe43cebf4bc3
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f669109c2773f4ba4df76e70fd708535cb13b33b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="functions-related-to-qnames---expanded-qname"></a>Funzioni correlate a elementi QName - expanded-QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce un valore di tipo xs: QName con lo spazio dei nomi specificato nell'URI di *$paramURI* e il nome locale specificato nella *$paramLocal*. Se *$paramURI* è una stringa vuota o una sequenza vuota, che rappresenta nessuno spazio dei nomi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
fn:expanded-QName($paramURI as xs:string?, $paramLocal as xs:string?) as xs:QName?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$paramURI*  
 URI dello spazio dei nomi dell'elemento QName.  
  
 *$paramLocal*  
 Parte dell'elemento QName che rappresenta il nome locale.  
  
## <a name="remarks"></a>Osservazioni  
 Nell'esempio si applica al **expanded-QName()** funzione:  
  
-   Se il *$paramLocal* valore specificato non è nella forma lessicale corretta per il tipo xs: NCName, la sequenza vuota, viene restituita e rappresenta un errore dinamico.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non supporta la conversione dal tipo xs:QName a un tipo diverso. Per questo motivo, il **expanded-QName()** funzione non può essere utilizzata nella costruzione di strutture XML. Ad esempio, quando si costruisce un nodo come `<e> expanded-QName(…) </e>`, il valore deve essere non tipizzato. A questo scopo è necessario convertire il valore del tipo xs:QName restituito da `expanded-QName()` in xdt:untypedAtomic. La funzionalità non è tuttavia supportata. Una soluzione a questo problema è illustrata in un esempio di seguito in questo argomento.  
  
-   È possibile modificare o confrontare i valori di tipo QName esistenti. Ad esempio, `/root[1]/e[1] eq expanded-QName("http://nsURI" "myNS")` confronta il valore dell'elemento, <`e`>, con l'elemento QName restituito dal **expanded-QName()** (funzione).  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo di [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.  
  
### <a name="a-replacing-a-qname-type-node-value"></a>A. Sostituzione di un valore di nodo di tipo QName  
 Nell'esempio seguente viene illustrata la procedura per modificare il valore di un nodo elemento di tipo QName. Nell'esempio vengono eseguite le operazioni seguenti:  
  
-   Crea una raccolta di XML Schema che definisce un elemento di tipo QName.  
  
-   Crea una tabella con un **xml** colonna di tipo mediante la raccolta di XML schema.  
  
-   Salva un'istanza XML nella tabella.  
  
-   Usa il **Modify ()** metodo del tipo di dati xml per modificare il valore dell'elemento di tipo QName nell'istanza. Il **expanded-QName()** funzione viene utilizzata per generare il nuovo valore di tipo QName.  
  
```  
-- If XML schema collection (if exists)  
-- drop xml schema collection SC  
-- go  
-- Create XML schema collection  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="QNameXSD"   
      xmlns:xqo="QNameXSD" elementFormDefault="qualified">  
      <element name="Root" type="xqo:rootType" />  
      <complexType name="rootType">  
            <sequence minOccurs="1" maxOccurs="1">  
                        <element name="ElemQN" type="xs:QName" />  
            </sequence>  
      </complexType>  
</schema>'  
go  
-- Create table.  
CREATE TABLE T( XmlCol xml(SC) )  
-- Insert sample XML instnace  
INSERT INTO T VALUES ('  
<Root xmlns="QNameXSD" xmlns:ns="http://myURI">  
      <ElemQN>ns:someName</ElemQN>  
</Root>')  
go  
-- Verify the insertion  
SELECT * from T  
go  
-- Result  
<Root xmlns="QNameXSD" xmlns:ns="http://myURI">  
  <ElemQN>ns:someName</ElemQN>  
</Root>   
```  
  
 Nella query seguente, il <`ElemQN`> valore dell'elemento viene sostituito con il **Modify ()** metodo del tipo di dati xml e il valore di sostituzione dell'istruzione DML XML, come illustrato.  
  
```  
-- the value.  
UPDATE T   
SET XmlCol.modify('  
  declare default element namespace "QNameXSD";   
  replace value of /Root[1]/ElemQN   
  with expanded-QName("http://myURI", "myLocalName") ')  
go  
-- Verify the result  
SELECT * from T  
go  
```  
  
 Di seguito è riportato il risultato. Si noti che l'elemento <`ElemQN`> di tipo QName ha ora un nuovo valore:  
  
```  
<Root xmlns="QNameXSD" xmlns:ns="urn">  
  <ElemQN xmlns:p1="http://myURI">p1:myLocalName</ElemQN>  
</Root>  
```  
  
 Le istruzioni seguenti rimuovono gli oggetti utilizzati nell'esempio.  
  
```  
-- Cleanup  
DROP TABLE T  
go  
drop xml schema collection SC  
go  
```  
  
### <a name="b-dealing-with-the-limitations-when-using-the-expanded-qname-function"></a>B. Gestione delle limitazioni di utilizzo della funzione expanded-QName()  
 Il **expanded-QName-** funzione non può essere utilizzata nella costruzione di strutture XML. Questa condizione è illustrata nell'esempio seguente. Per ovviare a questa limitazione, nell'esempio viene inserito per prima cosa un nodo, che verrà poi modificato.  
  
```  
-- if exists drop the table T  
--drop table T  
-- go  
-- Create XML schema collection  
-- DROP XML SCHEMA COLLECTION SC  
-- go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
 -- Create table T with a typed xml column (using the XML schema collection)  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- Insert an XML instance.  
insert into T values ('<root xmlns:a="http://someURI">a:b</root>')  
 go  
-- Verify  
SELECT *   
FROM T  
```  
  
 L'istruzione seguente tenta di aggiungere un nuovo elemento <`root`>, ma ha esito negativo perché la funzione expanded-QName() non è supportata nella costruzione di strutture XML.  
  
```  
update T SET xmlCol.modify('  
insert <root>{expanded-QName("http://ns","someLocalName")}</root> as last into / ')  
go  
```  
  
 Una soluzione consiste nell'inserire un'istanza con un valore per l'elemento <`root`> e quindi modificarla. In questo esempio quando viene inserito l'elemento <`root`> viene utilizzato un valore iniziale Null. La raccolta di XML Schema in questo esempio consente un valore Null per l'elemento <`root`>.  
  
```  
update T SET xmlCol.modify('  
insert <root xsi:nil="true"/> as last into / ')  
go  
-- now replace the nil value with another QName.  
update T SET xmlCol.modify('  
replace value of /root[last()] with expanded-QName("http://ns","someLocalName") ')  
go  
 -- verify   
SELECT * FROM T  
go  
-- result  
<root>b</root>  
```  
  
 `<root xmlns:a="http://someURI">a:b</root>`  
  
 `<root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:p1="http://ns">p1:someLocalName</root>`  
  
 È possibile confrontare il valore dell'elemento QName, come illustrato nella query seguente. La query restituisce solo il <`root`> gli elementi i cui valori corrispondono il nome completo del tipo valore restituito dal **expanded-QName()** (funzione).  
  
```  
SELECT xmlCol.query('  
    for $i in /root  
    return  
       if ($i eq expanded-QName("http://ns","someLocalName") ) then  
          $i  
       else  
          ()')  
FROM T  
```  
  
### <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Un limite: il **expanded-QName()** funzione accetta la sequenza vuota come secondo argomento e restituisce un valore vuoto invece di generare un errore di run-time quando il secondo argomento non è corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni correlate a elementi QName &#40;XQuery&#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
