---
title: Tipi di dati XPath (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d36d141e552750650ede74ba2aba92b203825558
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="xpath-data-types-sqlxml-40"></a>Tipi di dati XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath e gli elementi XML Schema (XSD) utilizzano tipi di dati molto diversi. XPath, ad esempio, non include tipi di dati integer o di data, mentre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e XSD ne includono diversi. XSD utilizza una precisione in nanosecondi per i valori di ora, mentre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza al massimo una precisione di 1/300 secondi. Di conseguenza, il mapping di un tipo di dati a un altro non è sempre possibile. Per ulteriori informazioni sul mapping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati a tipi di dati XSD, vedere [coercizioni dei tipi di dati e l'annotazione SQL: DataType &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath utilizza tre tipi di dati: **stringa**, **numero**, e **booleano**. Il **numero** tipo di dati è sempre una valore IEEE 754 a precisione doppia. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float (53)** tipo di dati è il più vicino a XPath **numero**. Tuttavia, **float (53)** non è esattamente IEEE 754. Ad esempio, non viene utilizzato né un valore diverso da un numero (NaN, Not-a-Number) né un valore infinito. Il tentativo di convertire una stringa di un valore numerico in **numero** e il tentativo di divisione per zero genera un errore.  
  
## <a name="xpath-conversions"></a>Conversioni XPath  
 Quando si utilizza una query XPath, ad esempio `OrderDetail[@UnitPrice > "10.0"]`, le conversioni dei tipi di dati implicite ed esplicite possono modificare impercettibilmente il significato della query. È pertanto importante comprendere le modalità di implementazione dei tipi di dati XPath. La specifica del linguaggio XPath, XML Path Language (XPath) version 1.0 W3C Proposed Recommendation 8 October 1999, è disponibile nel sito Web W3C all'indirizzo http://www.w3.org/TR/1999/PR-xpath-19991008.html.  
  
 Gli operatori XPath sono suddivisi in quattro categorie:  
  
-   Operatori booleani (and, or)  
  
-   Operatori relazionali (\<, >, \<=, > =)  
  
-   Operatori di uguaglianza (=, !=)  
  
-   Operatori aritmetici: (+, -, *, div, mod)  
  
 Ogni categoria di operatore converte in modo diverso gli operandi. Se necessario, gli operatori XPath convertono gli operandi in modo implicito. Operatori aritmetici convertono gli operandi in **numero**e il risultato in un valore numerico. Operatori booleani convertono gli operandi in **booleano**e il risultato in un valore booleano. Gli operatori relazionali e gli operatori di uguaglianza restituiscono un valore booleano, ma utilizzano regole di conversione diverse a seconda dei tipi di dati originali degli operandi, come illustrato nella tabella seguente.  
  
|Operando|Operatore relazionale|Operatore di uguaglianza|  
|-------------|-------------------------|-----------------------|  
|Entrambi gli operandi sono set di nodi.|TRUE se e solo se è presente un nodo in un set e un nodo nel secondo set ad che il confronto tra loro **stringa** valori è TRUE.|Idem|  
|Uno è un set di nodi, l'altro un **stringa**.|TRUE se e solo se è presente un nodo nel set di nodi in modo che quando convertito in **numero**, il confronto con il **stringa** convertito in **numero** è TRUE.|TRUE se e solo se è presente un nodo nel set di nodi in modo che quando convertito in **stringa**, il confronto con il **stringa** è TRUE.|  
|Uno è un set di nodi, l'altro un **numero**.|TRUE se e solo se è presente un nodo nel set di nodi in modo che quando convertito in **numero**, il confronto con il **numero** è TRUE.|Idem|  
|Uno è un set di nodi, l'altro un **booleano**.|TRUE se e solo se è presente un nodo nel set di nodi in modo che quando convertito in **booleano** e quindi a **numero**, il confronto con il **booleano** convertito in **numero** è TRUE.|TRUE se e solo se è presente un nodo nel set di nodi in modo che quando convertito in **booleano**, il confronto con il **booleano** è TRUE.|  
|Nessuno è un set di nodi.|Convertire entrambi gli operandi in **numero** e mettere a confronto.|Convertire entrambi gli operandi in un tipo comune e quindi eseguire il confronto. Convertire **booleano** in presenza di una **booleano**, **numero** in presenza di una **numero**; in caso contrario, convertire **stringa**.|  
  
> [!NOTE]  
>  Poiché gli operatori relazionali XPath convertono sempre gli operandi in **numero**, **stringa** confronti non sono possibili. Per includere il confronto di date, SQL Server 2000 è disponibile una variazione alla specifica XPath: quando un operatore relazionale Confronta un **stringa** per un **stringa**, un set di nodi un **stringa**, o un stringa con valori di set di nodi in un stringa con valori di set di nodi, un **stringa** confronto (non un **numero** confronto) viene eseguita.  
  
## <a name="node-set-conversions"></a>Conversioni dei set di nodi  
 Le conversioni dei set di nodi non sono sempre intuitive. Un set di nodi viene convertito in un **stringa** prendendo il valore di stringa di solo il primo nodo nel set. Un set di nodi viene convertito in **numero** tramite la conversione a **stringa**e quindi la conversione **stringa** a **numero**. Un set di nodi viene convertito in **booleano** eseguendo i test di esistenza.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non esegue selezione della posizione nel set di nodi: ad esempio, la query XPath `Customer[3]` indica il terzo cliente; questo tipo di selezione della posizione non è supportato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Di conseguenza, il nodo-set-per-**stringa** o nodo-set-per-**numero** conversioni come descritto dalla specifica XPath non sono implementate. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza le semantiche "any" dove la specifica XPath specifica la semantica "first". Ad esempio, in base alla specifica W3C XPath, la query XPath `Order[OrderDetail/@UnitPrice > 10.0]` seleziona gli ordini con il primo **OrderDetail** che ha un **UnitPrice** maggiore di 10.0. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questa query XPath seleziona gli ordini con qualsiasi **OrderDetail** che ha un **UnitPrice** maggiore di 10.0.  
  
 La conversione a **booleano** genera un esistenza test; pertanto, la query XPath `Products[@Discontinued=true()]` equivale all'espressione SQL "Products. Discontinued is not null", non all'espressione SQL "Products. Discontinued = 1". Per rendere la query è equivalente all'espressione SQL, convertire innanzitutto il set di nodi in un non -**booleano** digitare, ad esempio **numero**. Ad esempio, `Products[number(@Discontinued) = true()]`.  
  
 Poiché la maggior parte degli operatori viene definita come TRUE se gli operatori sono TRUE per tutti i nodi nel set di nodi o per uno di essi, queste operazioni restituiscono sempre FALSE se il set di nodi è vuoto. In questo modo, se A è vuoto, sia `A = B` sia `A != B` sono FALSE e `not(A=B)` e `not(A!=B)` sono TRUE.  
  
 In genere, esiste un attributo o elemento che esegue il mapping a una colonna se il valore della colonna nel database non è **null**. Sono presenti elementi di cui è stato eseguito il mapping a righe se è presente uno qualunque dei figli.  
  
> [!NOTE]  
>  Gli elementi annotati con **costante è** esiste sempre. Di conseguenza, i predicati XPath non possono essere utilizzati in **costante è** elementi.  
  
 Quando un set di nodi viene convertito in **stringa** o **numero**, il tipo XDR (se presente) viene controllato nello schema con annotazioni e tale tipo viene utilizzato per determinare la conversione necessaria.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Mapping di tipi di dati XDR a tipi di dati XPath  
 Il tipo di dati XPath di un nodo viene derivato dal tipo di dati XDR nello schema, come illustrato nella tabella seguente (il nodo **EmployeeID** viene utilizzato a scopo illustrativo).  
  
|Tipo di dati XDR|Equivalente<br /><br /> Tipo di dati XPath|Conversione SQL Server utilizzata|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|N/D|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float, i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|number|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/D (in XPath non è disponibile alcun tipo di dati equivalente al tipo di dati XDR fixed14.4).|CONVERT(money, EmployeeID)|  
|data|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Le conversioni di data e ora sono progettate per funzionare se il valore viene archiviato nel database utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** tipo di dati o un **stringa**. Si noti che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** tipo di dati non utilizza **fuso orario** e ha una precisione minore rispetto a XML **ora** tipo di dati. Per includere il **fuso orario** tipo di dati o aggiungere ulteriore precisione, archiviare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando un **stringa** tipo.  
  
 Quando un nodo viene convertito dal relativo tipo di dati XDR al tipo di dati XPath, è talvolta necessaria un'ulteriore conversione (da un tipo di dati XPath a un altro tipo di dati XPath). Si consideri, ad esempio, la query XPath seguente:  
  
```  
(@m + 3) = 4  
```  
  
 Se @m è il **fixed 14.4** tipo di dati XDR, la conversione dal tipo di dati XDR al tipo di dati viene eseguito con XPath:  
  
```  
CONVERT(money, m)  
```  
  
 In questa conversione, il nodo `m` viene convertito da **fixed 14.4** a **money**. Per aggiungere il valore 3, tuttavia, è necessaria un'ulteriore conversione:  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 L'espressione XPath viene valutata nel modo seguente:  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 Come illustrato nella tabella seguente, si tratta della stessa conversione applicata per altre espressioni XPath, ad esempio i valori letterali o le espressioni composte.  
  
||||||  
|-|-|-|-|-|  
||X non è noto|X è **stringa**|X è **numero**|X è **booleano**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) > 0|X != 0|-|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. Convertire un tipo di dati in una query XPath  
 Nella query XPath seguente specificata su uno schema XSD con annotazioni, la query Seleziona tutti **dipendente** nodi con il **EmployeeID** attributo valore 1 per, dove "E-" è il prefisso specificato utilizzando il **SQL: ID-prefisso** annotazione.  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Il predicato nella query equivale all'espressione SQL:  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 Poiché **EmployeeID** è uno del **id** (**idref**, **idrefs**, **nmtoken**,  **NMTOKENS**e così via) i valori del tipo di dati nello schema XSD, **EmployeeID** viene convertito nel **stringa** il tipo di dati XPath utilizzando le regole di conversione descritte in precedenza.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Il prefisso "E-" viene aggiunto alla stringa, e il risultato viene quindi confrontato con `N'E-1'`.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. Eseguire diverse conversioni dei tipi di dati in una query XPath  
 Considerare la seguente query XPath specificata su uno schema XSD con annotazioni: `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Questa query XPath restituisce tutti i  **\<OrderDetail >** gli elementi che soddisfano il predicato `@UnitPrice * @OrderQty > 98`. Se il **UnitPrice** è annotato con un **fixed 14.4** del tipo di dati nello schema con annotazioni, questo predicato equivale all'espressione SQL:  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Nel convertire i valori nella query XPath, la prima operazione converte il tipo di dati XDR nel tipo di dati XPath. Poiché il tipo di dati XSD di **UnitPrice** è **fixed 14.4**, come descritto nella tabella precedente, questa è la prima conversione utilizzata:  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Poiché gli operatori aritmetici convertono gli operandi per il **numero** il tipo di dati XPath, la seconda conversione (da un tipo di dati XPath a un altro tipo di dati XPath) viene applicata in cui il valore viene convertito in **float (53)**  (**float (53)** è vicino a XPath **numero** tipo di dati):  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Supponendo che il **OrderQty** attributo non dispone di alcun tipo di dati XSD, **OrderQty** viene convertito in un **numero** il tipo di dati XPath in una singola conversione:  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 Analogamente, il valore 98 viene convertito nel **numero** tipo di dati XPath:  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Se il tipo di dati XSD utilizzato nello schema non è compatibile con il tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottostante nel database o se viene eseguita una conversione del tipo di dati XPath non consentita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può restituire un errore. Ad esempio, se il **EmployeeID** attributo viene annotato con **id-prefix** annotazione, l'espressione XPath `Employee[@EmployeeID=1]` genera un errore, perché **EmployeeID** ha il **id-prefix** annotazione e non può essere convertito in **numero**.  
  
  
