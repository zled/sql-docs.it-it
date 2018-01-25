---
title: Clausola FOR (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FOR
- FOR CLAUSE
- FOR_TSQL
- FOR_CLAUSE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- XML option [SQL Server]
- BROWSE option
- FOR clause [Transact-SQL]
ms.assetid: 08a6f084-8f73-4f2a-bae4-3c7513dc99b9
caps.latest.revision: "54"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 085a9c7f6422c70cc43086d2174a5c7aa485040e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="select---for-clause-transact-sql"></a>SELECT - clausola FOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Utilizzare la clausola FOR per specificare una delle seguenti opzioni dei risultati della query.  
  
-   Consenti aggiornamenti durante la visualizzazione dei risultati della query in un cursore di modalità browse specificando **FOR BROWSE**.  
  
-   Formattare i risultati della query come XML specificando **FOR XML**.  
  
-   Formattare i risultati della query come JSON specificando **FOR JSON**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
[ FOR { BROWSE | <XML> | <JSON>} ]  
  
<XML> ::=  
XML   
{   
    { RAW [ ( 'ElementName' ) ] | AUTO }   
    [   
        <CommonDirectivesForXML>   
        [ , { XMLDATA | XMLSCHEMA [ ( 'TargetNameSpaceURI' ) ] } ]   
        [ , ELEMENTS [ XSINIL | ABSENT ]   
    ]  
  | EXPLICIT   
    [   
        <CommonDirectivesForXML>   
        [ , XMLDATA ]   
    ]  
  | PATH [ ( 'ElementName' ) ]   
    [  
        <CommonDirectivesForXML>   
        [ , ELEMENTS [ XSINIL | ABSENT ] ]  
    ]  
}   
  
<CommonDirectivesForXML> ::=   
[ , BINARY BASE64 ]  
[ , TYPE ]  
[ , ROOT [ ( 'RootName' ) ] ]  
  
<JSON> ::=  
JSON   
{   
    { AUTO | PATH }   
    [   
        [ , ROOT [ ( 'RootName' ) ] ]  
        [ , INCLUDE_NULL_VALUES ]  
        [ , WITHOUT_ARRAY_WRAPPER ]  
    ]  
  
}  
```  
  
## <a name="for-browse"></a>FOR BROWSE  
 BROWSE  
 Specifica che è possibile eseguire aggiornamenti durante la visualizzazione dei dati in un cursore DB-Library in modalità browse. Una tabella può essere visualizzata in un'applicazione se la tabella include un **timestamp** colonna, la tabella include un indice univoco e l'opzione FOR BROWSE si trova alla fine delle istruzioni SELECT inviate a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Non è possibile utilizzare il \<lock_hint > HOLDLOCK in un'istruzione SELECT che include l'opzione FOR BROWSE.
  
 L'opzione FOR BROWSE non è supportata in istruzioni SELECT unite con l'operatore UNION.  
  
> [!NOTE]  
>  Quando le colonne chiave indice univoco di una tabella ammettono valori Null e la tabella si trova sul lato interno di un outer join, l'indice non è supportato dalla modalità browse.  
  
 La modalità browse consente di analizzare le righe nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e di aggiornarne i relativi dati una riga alla volta. Per accedere a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella nell'applicazione in modalità browse, è necessario utilizzare una delle due opzioni seguenti:  
  
-   L'istruzione SELECT che consente di accedere ai dati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella deve terminare con le parole chiave **FOR BROWSE**. Quando si attiva il **FOR BROWSE** opzione per utilizzare la modalità browse, vengono create le tabelle temporanee.  
  
-   È necessario eseguire le operazioni seguenti [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione per attivare la modalità browse mediante il **NO_BROWSETABLE** opzione:  
  
    ```  
    SET NO_BROWSETABLE ON  
    ```  
  
     Quando si attiva il **NO_BROWSETABLE** opzione, tutte le istruzioni SELECT si comportano come se il **FOR BROWSE** opzione viene aggiunto alle istruzioni. Tuttavia, il **NO_BROWSETABLE** opzione non crea le tabelle temporanee che il **FOR BROWSE** opzione in genere viene utilizzata per inviare i risultati all'applicazione.  
  
 Quando si tenta di accedere ai dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle in modalità browse utilizzando una query SELECT che include un'istruzione outer join e quando un indice univoco viene definito nella tabella che è presente nel lato interno di un'istruzione outer join, la modalità browse non sup porta l'indice univoco. L'indice univoco viene supportato solo quando tutte le colonne chiave possono accettare valori null. Non viene supportato, invece, in presenza delle condizioni seguenti:  
  
-   Si tenta di accedere ai dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle in modalità browse utilizzando una query SELECT che include un'istruzione outer join.  
  
-   Un indice univoco viene definito nella tabella presente sul lato interno di un'istruzione outer join.  
  
 Per riprodurre questo comportamento in modalità browse, effettuare le operazioni seguenti:  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creare un database, denominato SampleDB.  
  
2.  Nel database SampleDB, creare una tabella tleft e una tabella tright, contenenti entrambe una sola colonna denominata c1. Definire un indice univoco sulla colonna c1 nella tabella tleft e impostare la colonna affinché accetti valori null. A tale scopo, eseguire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti in una finestra di query appropriata:  
  
    ```  
    CREATE TABLE tleft(c1 INT NULL UNIQUE) ;  
    GO   
    CREATE TABLE tright(c1 INT NULL) ;  
    GO  
    ```  
  
3.  Inserire diversi valori nelle tabelle tleft e tright. Verificare che nella tabella tleft venga inserito un valore null. A tale scopo, eseguire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti nella finestra di query:  
  
    ```  
    INSERT INTO tleft VALUES(2) ;  
    INSERT INTO tleft VALUES(NULL) ;  
    INSERT INTO tright VALUES(1) ;  
    INSERT INTO tright VALUES(3) ;  
    INSERT INTO tright VALUES(NULL) ;  
    GO  
    ```  
  
4.  Accendere il **NO_BROWSETABLE** opzione. A tale scopo, eseguire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti nella finestra di query:  
  
    ```  
    SET NO_BROWSETABLE ON ;  
    GO  
    ```  
  
5.  Accedere ai dati nelle tabelle tleft e tright utilizzando un'istruzione outer join nella query SELECT. Verificare che la tabella tleft si trovi nel lato interno dell'istruzione outer join. A tale scopo, eseguire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti nella finestra di query:  
  
    ```  
    SELECT tleft.c1   
    FROM tleft   
    RIGHT JOIN tright   
    ON tleft.c1 = tright.c1   
    WHERE tright.c1 <> 2 ;  
  
    ```  
  
     Notare l'output seguente nel riquadro Risultati:  
  
     c1  
  
     ---\-  
  
     NULL  
  
     NULL  
  
 Dopo avere eseguito la query SELECT per accedere alle tabelle in modalità browse, il set di risultati della query SELECT contiene due valori null per la colonna c1 nella tabella tleft a causa della definizione dell'istruzione right outer join. Nel set di risultati non sarà pertanto possibile distinguere tra i valori null provenienti dalla tabella e i valori null introdotti dall'istruzione right outer join. Se è necessario ignorare i valori null dal set di risultati, è possibile che si ottengano risultati errati.  
  
> [!NOTE]  
>  Se le colonne incluse nell'indice univoco non accettano valori null, tutti i valori null nel set di risultati sono stati introdotti dall'istruzione right outer join.  
  
## <a name="for-xml"></a>FOR XML  
 XML  
 Specifica che i risultati di una query devono essere restituiti come documento XML. È necessario specificare una della modalità XML seguenti: RAW, AUTO o EXPLICIT. Per ulteriori informazioni sui dati XML e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [FOR XML &#40; SQL Server &#41; ](../../relational-databases/xml/for-xml-sql-server.md).  
  
 Non ELABORATO [ **('***ElementName***')** ]  
 Accetta il risultato della query e converte ogni riga di set di risultati in un elemento XML con l'identificatore generico \<righe / > come tag dell'elemento. È possibile specificare facoltativamente un nome per l'elemento riga. L'output XML risultante utilizza l'oggetto specificato *ElementName* come elemento riga generato per ogni riga. Per ulteriori informazioni, vedere [usare la modalità RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md) e [usare la modalità RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 AUTO  
 Restituisce i risultati della query in un semplice albero XML nidificato. Ogni tabella nella clausola FROM, per cui è specificata almeno una colonna nella clausola SELECT, viene rappresentata come elemento XML. Le colonne elencate nella clausola SELECT vengono mappate agli attributi di elemento appropriati. Per altre informazioni, vedere [Usare la modalità AUTO con FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
 EXPLICIT  
 Specifica che la forma dell'albero XML risultante viene definita in modo esplicito. Con questa modalità è tuttavia necessario che le query siano scritte in modo che le informazioni aggiuntive sulla nidificazione desiderata siano specificate in modo esplicito. Per altre informazioni, vedere [Usare la modalità EXPLICIT con FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md).  
  
 XMLDATA  
 Restituisce lo schema XDR inline, ma non aggiunge l'elemento radice al risultato. Se si specifica l'opzione XMLDATA, lo schema XDR viene aggiunto al documento.  
  
> [!IMPORTANT]  
>  La direttiva XMLDATA è deprecata. Utilizzare la generazione XSD in caso di modalità RAW e AUTO. Non sono disponibili sostituzioni per direttiva XMLDATA in modalità EXPLICIT. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 XMLSCHEMA [ **('***TargetNameSpaceURI***')** ]  
 Restituisce lo schema XSD inline. Quando si utilizza questa direttiva è possibile specificare facoltativamente un URI dello spazio dei nomi di destinazione, che restituisce lo spazio dei nomi specificato nello schema. Per altre informazioni, vedere [Generare uno schema XSD inline](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
 ELEMENTS  
 Specifica che le colonne devono essere restituite come sottoelementi. In caso contrario, vengono mappate ad attributi XML. Questa opzione è supportata solo con le modalità RAW, AUTO e PATH. Per altre informazioni, vedere [Usare la modalità RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 XSINIL  
 Specifica che un elemento con **xsi: nil** attributo impostato su **True** creato per valori di colonna NULL. È possibile specificare questa opzione solo con la direttiva ELEMENTS. Per ulteriori informazioni, vedere [generare elementi per i valori NULL con il parametro XSINIL](../../relational-databases/xml/generate-elements-for-null-values-with-the-xsinil-parameter.md).  
  
 ABSENT  
 Indica che per i valori di colonna NULL non verranno aggiunti elementi XML corrispondenti nel risultato XML. Specificare questa opzione solo con ELEMENTS.  
  
 PERCORSO [ **('***ElementName***')** ]  
 Genera un \<riga > wrapper dell'elemento per ogni riga nel set di risultati. È possibile specificare facoltativamente un nome di elemento per il \<riga > wrapper dell'elemento. Se viene fornita una stringa vuota, ad esempio di FOR XML PATH (**'**)), non viene generato un elemento wrapper. L'utilizzo di PATH può rappresentare un'alternativa più semplice alla scrittura di query con la direttiva EXPLICIT. Per altre informazioni, vedere [Usare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md).  
  
 BINARY BASE64  
 Specifica che la query restituisce i dati binari nel formato binario con codifica Base64. Per recuperare dati binari utilizzando la modalità RAW ed EXPLICIT, questa opzione deve essere specificata. Corrisponde all'impostazione predefinita in modalità AUTO.  
  
 TYPE  
 Specifica che la query restituisce risultati come **xml** tipo. Per altre informazioni, vedere [Direttiva TYPE nelle query FOR XML](../../relational-databases/xml/type-directive-in-for-xml-queries.md).  
  
 RADICE [ **('***RootName***')** ]  
 Specifica l'aggiunta di un singolo elemento principale al documento XML risultante. È possibile specificare facoltativamente il nome dell'elemento radice da generare. Se il nome radice non è specificato, il valore predefinito \<radice > viene aggiunto l'elemento.  
  
 Per altre informazioni, vedere [FOR XML &#40; SQL Server &#41; ](../../relational-databases/xml/for-xml-sql-server.md).  
  
 **AD esempio XML**  
  
 Nell'esempio seguente la clausola `FOR XML AUTO` viene specificata con le opzioni `TYPE` e `XMLSCHEMA`. Perché il `TYPE` opzione, il set di risultati viene restituito al client come un **xml** tipo. L'opzione `XMLSCHEMA` imposta l'aggiunta dello schema XSD inline nei dati XML restituiti e l'opzione `ELEMENTS` specifica che il risultato XML è incentrato sugli elementi.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT p.BusinessEntityID, FirstName, LastName, PhoneNumber AS Phone  
FROM Person.Person AS p  
JOIN Person.PersonPhone AS pph ON p.BusinessEntityID  = pph.BusinessEntityID  
WHERE LastName LIKE 'G%'  
ORDER BY LastName, FirstName   
FOR XML AUTO, TYPE, XMLSCHEMA, ELEMENTS XSINIL;  
```  
  
## <a name="for-json"></a>FOR JSON  
 JSON  
 Specificare la clausola FOR JSON per restituire i risultati di una query formattati come testo JSON. È inoltre necessario specificare una delle seguenti modalità di JSON: automaticamente o il percorso. Per ulteriori informazioni sul **FOR JSON** clausola, vedere [formattare i risultati delle Query come JSON con FOR JSON &#40; SQL Server &#41; ](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 AUTO  
 Formato di output JSON automaticamente in base alla struttura del **selezionare** istruzione  
            specificando **FOR JSON AUTO**. Per altre informazioni ed esempi, vedere [Formattare automaticamente l'output JSON con la modalità AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).  
  
 PATH  
 Ottenere il controllo completo sul formato dell'output JSON specificando   
            **FOR JSON PATH**. La modalità**PATH** consente di creare oggetti wrapper e annidare proprietà complesse. Per altre informazioni ed esempi, vedere [Formattare l'output JSON annidato con la modalità PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).  
  
 INCLUDE_NULL_VALUES  
 Includere valori null nell'output JSON, specificando il **INCLUDE_NULL_VALUES** con il **FOR JSON** clausola. Se non si specifica questa opzione, l'output non include le proprietà JSON per i valori null nei risultati della query. Per ulteriori informazioni ed esempi, vedere [includono valori Null nell'Output JSON con l'opzione INCLUDE_NULL_VALUES &#40; SQL Server &#41; ](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).  
  
 RADICE [ **('***RootName***')** ]  
 Aggiungere un singolo elemento di primo livello all'output JSON, specificando il **radice** con il **FOR JSON** clausola. Se non si specifica l'opzione **ROOT** , l'output JSON non avrà alcun elemento radice. Per ulteriori informazioni ed esempi, vedere [aggiungere un nodo radice all'Output JSON con l'opzione ROOT &#40; SQL Server &#41; ](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
 WITHOUT_ARRAY_WRAPPER  
 Rimuovere le parentesi quadre che racchiudono l'output JSON per impostazione predefinita, specificando il **WITHOUT_ARRAY_WRAPPER** con il **FOR JSON** clausola. Se non si specifica questa opzione, l'output JSON è racchiuso tra parentesi quadre. Utilizzare il **WITHOUT_ARRAY_WRAPPER** opzione per generare un singolo oggetto JSON come output.  Per altre informazioni, vedere [Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option &#40;SQL Server&#41; (Rimuovere le parentesi quadre dall'output JSON con l'opzione WITHOUT_ARRAY_WRAPPER &#40;SQL Server&#41;)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md).  
  
 Per altre informazioni, vedere [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
