---
title: sp_xml_preparedocument (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_xml_preparedocument_TSQL
- sp_xml_preparedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_preparedocument
ms.assetid: 95f41cff-c52a-4182-8ac6-bf49369d214c
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 911d6dd9613803aff79187a22f4ebf6bc0b7a4cc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spxmlpreparedocument-transact-sql"></a>sp_xml_preparedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legge il testo in formato XML specificato come input, ne esegue l'analisi mediante il parser MSXML (Msxmlsql.dll) e restituisce il documento analizzato in un formato pronto per l'uso. Il documento analizzato corrisponde a una rappresentazione ad albero dei vari nodi (elementi, attributi, testo, commenti e così via) del documento XML.  
  
 **sp_xml_preparedocument** restituisce un handle che può essere utilizzato per accedere la nuova rappresentazione interna del documento XML. Questo handle è valido per la durata della sessione o finché non viene invalidato l'handle eseguendo **sp_xml_removedocument**.  
  
> [!NOTE]  
>  Un documento analizzato viene archiviato nella cache interna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il parser MSXML utilizza un ottavo della memoria totale disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per evitare di esaurire la memoria, eseguire **sp_xml_removedocument** per liberare la memoria.  
  
> [!NOTE]  
>  Per garantire la compatibilità, **sp_xml_preparedocument** comprime i caratteri CR (char(13)) e avanzamento riga (caratteri char(10)) negli attributi anche se questi caratteri vengono sostituiti con entità.  
  
> [!NOTE]  
>  Il parser XML richiamato da **sp_xml_preparedocument** consente di analizzare le dichiarazioni di entità e definizioni DTD interne. Perché è stato costruito da utenti malintenzionati le DTD ed entità dichiarazioni possono essere utilizzate per eseguire un attacco denial of service, è consigliabile che gli utenti non vengano passati direttamente documenti XML da origini non attendibili **sp_xml_preparedocument**.  
>   
>  Per ridurre gli attacchi espansione di entità ricorsiva, **sp_xml_preparedocument** limita a 10.000 il numero di entità che possono essere espansi sotto una singola entità al livello superiore di un documento. Tale limite non viene applicato a entità carattere o numeriche e consente di archiviare documenti con numerosi riferimenti a entità impedendo tuttavia l'espansione ricorsiva di qualsiasi entità in una catena di lunghezza superiore a 10.000 espansioni.  
  
> [!NOTE]  
>  **sp_xml_preparedocument** limita il numero di elementi che possono essere aperti contemporaneamente a 256.  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_xml_preparedocument  
hdoc   
OUTPUT  
[ , xmltext ]  
[ , xpath_namespaces ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *hdoc*  
 Handle del nuovo documento. *hdoc* è un numero intero.  
  
 [ *xmltext* ]  
 Documento XML originale. Il parser MSXML analizza il documento XML. *XmlText* è un parametro di testo: **char**, **nchar**, **varchar**, **nvarchar**, **testo**, **ntext** oppure **xml**. Il valore predefinito è NULL, con cui viene creata una rappresentazione interna di un documento XML vuoto.  
  
> [!NOTE]  
>  **sp_xml_preparedocument** può elaborare solo testo o XML non tipizzato. Se un valore istanza da utilizzare come input è già XML tipizzato, eseguire innanzitutto il cast di tale valore in una nuova istanza XML non tipizzata oppure come stringa, quindi passare il valore come input. Per altre informazioni, vedere [Confrontare dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
 [ *xpath_namespaces* ]  
 Specifica le dichiarazioni degli spazi dei nomi utilizzate nelle espressioni XPath di riga e colonna in OPENXML. *xpath_namespaces* è un parametro di testo: **char**, **nchar**, **varchar**, **nvarchar**, **testo**, **ntext** o **xml**.  
  
 Il valore predefinito è  **\<radice xmlns:mp = "urn: schemas-microsoft-com: xml-metaprop" >**. *xpath_namespaces* fornisce l'URI dello spazio dei nomi per i prefissi utilizzati nelle espressioni XPath in OPENXML tramite un documento XML ben formato. *xpath_namespaces* dichiara il prefisso che deve essere utilizzato per fare riferimento allo spazio dei nomi **urn: schemas-microsoft-com: xml-metaprop**; in questo modo i metadati relativi a elementi XML analizzati. Questa tecnica consente di ridefinire il prefisso dello spazio dei nomi di metaproprietà conservando allo stesso tempo lo spazio dei nomi. Il prefisso **mp** è ancora valido per **urn: schemas-microsoft-com: xml-metaprop** anche se *xpath_namespaces* non contiene tale dichiarazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-preparing-an-internal-representation-for-a-well-formed-xml-document"></a>A. Preparazione di una rappresentazione interna di un documento XML  
 Nell'esempio seguente viene restituito un handle per la nuova rappresentazione interna del documento XML specificato come input. Nella chiamata a `sp_xml_preparedocument` viene utilizzato il mapping predefinito per i prefissi degli spazi dei nomi.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
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
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
-- Remove the internal representation.  
exec sp_xml_removedocument @hdoc;  
```  
  
### <a name="b-preparing-an-internal-representation-for-a-well-formed-xml-document-with-a-dtd"></a>B. Preparazione di una rappresentazione interna di un documento XML con DTD  
 Nell'esempio seguente viene restituito un handle per la nuova rappresentazione interna del documento XML specificato come input. Il documento caricato viene convalidato in base al valore DTD incluso nel documento. Nella chiamata a `sp_xml_preparedocument` viene utilizzato il mapping predefinito per i prefissi degli spazi dei nomi.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(2000);  
SET @doc = '  
<?xml version="1.0" encoding="UTF-8" ?>   
<!DOCTYPE root   
[<!ELEMENT root (Customers)*>  
<!ELEMENT Customers EMPTY>  
<!ATTLIST Customers CustomerID CDATA #IMPLIED ContactName CDATA #IMPLIED>]>  
<root>  
<Customers CustomerID="ALFKI" ContactName="Maria Anders"/>  
</root>';  
  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
```  
  
### <a name="c-specifying-a-namespace-uri"></a>C. Specificazione di URI di spazi dei nomi  
 Nell'esempio seguente viene restituito un handle per la nuova rappresentazione interna del documento XML specificato come input. La chiamata a `sp_xml_preparedocument` mantiene il `mp` come prefisso per il mapping dello spazio dei nomi di metaproprietà e aggiunge il `xyz` prefisso di mapping allo spazio dei nomi `urn:MyNamespace`.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc, '<ROOT xmlns:xyz="urn:MyNamespace"/>';  
```  
  
## <a name="see-also"></a>Vedere anche  
 <br>[XML archiviati Procedures(Transact-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[Sistema archiviati Procedures(Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[OPENXML(Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
 <br>[Sys.dm_exec_xml_handles (Transact-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_removedocument (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)
  
  
