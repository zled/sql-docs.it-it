---
title: Formattare i risultati delle query in formato JSON con FOR JSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON
- JSON, exporting
- exporting JSON
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c439a76e3e925d00e88adaaefa616e59f8529a40
ms.lasthandoff: 04/11/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Formattare i risultati delle query in formato JSON con FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

È possibile formattare i risultati delle query come JSON o esportare i dati da SQL Server in formato JSON aggiungendo la clausola **FOR JSON** a un'istruzione **SELECT** . Usare la clausola **FOR JSON** per delegare la formattazione dell'output JSON dalle applicazioni client a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
 Quando si usa la clausola **FOR JSON** , è possibile specificare la struttura dell'output in modo esplicito o determinarla automaticamente in base alla struttura dell'istruzione SELECT.  
  
-   Usare la modalità **PATH** con la clausola **FOR JSON** per mantenere il controllo completo sul formato dell'output JSON. È possibile creare oggetti wrapper e annidare proprietà complesse.  
  
-   Usare l'opzione **AUTO** con la clausola **FOR JSON** per formattare l'output JSON automaticamente in base alla struttura dell'istruzione SELECT.  
  
Di seguito è riportato un esempio di istruzione **SELECT** con la clausola **FOR JSON** e il relativo output.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## <a name="maintain-control-over-json-output-with-path-mode"></a>Mantenere il controllo sull'output JSON con la modalità PATH  
In modalità **PATH** è possibile formattare l'output annidato usando la sintassi con il punto, ad esempio `'Item.Price'` . L'esempio seguente usa anche l'opzione **ROOT** per specificare un elemento radice denominato.  

Ecco una query di esempio che usa la modalità **PATH** con la clausola **FOR JSON** .
  
 ![Diagramma di flusso dell'output FOR JSON](../../relational-databases/json/media/forjson-example1.png "Diagramma di flusso dell'output FOR JSON")  

### <a name="more-info"></a>Altre informazioni
Per altre informazioni ed esempi, vedere [Formattare l'output JSON annidato con la modalità PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Per la sintassi e l'uso, vedere [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="let-the-select-statement-control-json-output-with-auto-mode"></a>Consentire all'istruzione SELECT di controllare l'output JSON con la modalità AUTO  
In modalità **AUTO** il formato dell'output JSON è determinato dalla struttura dell'istruzione SELECT. Per impostazione predefinita, i valori **null** non vengono inclusi nell'output. È possibile usare **INCLUDE_NULL_VALUES** per modificare questo comportamento.  

Ecco una query di esempio che usa la modalità **AUTO** con la clausola **FOR JSON** .
 
**Query:**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **Risultati**  
  
```json  
[{
    "name": "John"
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```  
### <a name="more-info"></a>Altre informazioni
Per altre informazioni ed esempi, vedere [Formattare automaticamente l'output JSON con la modalità AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Per la sintassi e l'uso, vedere [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Controllare altre opzioni di output JSON  
 Per controllare l'output della clausola **FOR JSON** è possibile usare le opzioni seguenti.  
  
-   Per aggiungere un unico elemento di primo livello all'output JSON, specificare l'opzione **ROOT** . Se non si specifica l'opzione **ROOT** , l'output JSON non avrà alcun elemento radice. Per altre informazioni, vedere [Add a Root Node to JSON Output with the ROOT Option &#40;SQL Server&#41; (Aggiungere un nodo radice all'output JSON con l'opzione ROOT &#40;SQL Server&#41;)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   Per includere valori Null nell'output JSON, specificare l'opzione **INCLUDE_NULL_VALUES** . Se non si specifica questa opzione, l'output non includerà le proprietà JSON per i valori NULL presenti nei risultati della query. Per altre informazioni, vedere[Include Null Values in JSON Output with the INCLUDE_NULL_VALUES Option &#40;SQL Server&#41; (Includere valori Null nell'output JSON con l'opzione INCLUDE_NULL_VALUES &#40;SQL Server&#41;)](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   Per rimuovere le parentesi quadre che racchiudono l'output JSON della clausola **FOR JSON** per impostazione predefinita, specificare l'opzione **WITHOUT_ARRAY_WRAPPER** . Usare questa opzione per generare un singolo oggetto JSON come output. Se non si specifica questa opzione, l'output JSON è racchiuso tra parentesi quadre. Per altre informazioni, vedere [Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option &#40;SQL Server&#41; (Rimuovere le parentesi quadre dall'output JSON con l'opzione WITHOUT_ARRAY_WRAPPER &#40;SQL Server&#41;)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Output della clausola FOR JSON  
 L'output della clausola **FOR JSON** ha le caratteristiche seguenti.  
  
1.  Il set di risultati contiene un'unica colonna. Un set di risultati di piccole dimensioni può contenere un'unica riga. Un set di risultati di grandi dimensioni contiene più righe.  
  
     ![Esempio di output FOR JSON](../../relational-databases/json/media/forjson-example2.png "Esempio di output FOR JSON")  
  
2.  I risultati vengono formattati sotto forma di matrice di oggetti JSON.  
  
    -   Il numero di elementi della matrice è uguale al numero delle righe nei risultati.  
  
    -   All'interno della matrice ogni riga del set di risultati diventa un oggetto JSON separato.  
  
    -   Ogni colonna nel set di risultati diventa una proprietà dell'oggetto JSON.  
  
3.  I nomi delle colonne e i valori corrispondenti vengono sottoposti a escape in base alla sintassi JSON. Per altre informazioni, vedere [How FOR JSON escapes special characters and control characters &#40;SQL Server&#41; (Sequenze di escape FOR JSON per i caratteri speciali e di controllo &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).
  
 Ecco un esempio che illustra la formattazione dell'output JSON.  
  
 **Risultati query**  
  
|||||  
|-|-|-|-|  
|**A**|**B**|**C**|**D**|  
|10|11|12|X|  
|20|21|22|S|  
|30|31|32|Z|  
  
 **Output JSON**  
  
```json  
[{
    "A": 10,
    "B": 11,
    "C": 12,
    "D": "X"
}, {
    "A": 20,
    "B": 21,
    "C": 22,
    "D": "Y"
}, {
    "A": 30,
    "B": 31,
    "C": 32,
    "D": "Z"
}] 
```  
 Per altre informazioni su quanto visualizzato nell'output della clausola **FOR JSON** , vedere gli argomenti seguenti.  
-   [How FOR JSON converts SQL Server data types to JSON data types &#40;SQL Server&#41; (Conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
La clausola **FOR JSON** usa le regole descritte in questo argomento per convertire i tipi di dati SQL in tipi di dati JSON nell'output JSON.  

-   [How FOR JSON escapes special characters and control characters &#40;SQL Server&#41; (Sequenze di escape FOR JSON per i caratteri speciali e di controllo &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 La clausola **FOR JSON** usa sequenze di escape per i caratteri speciali e rappresenta i caratteri di controllo nell'output JSON come descritto in questo argomento.  

## <a name="learn-more-about-for-json-and-built-in-json-support-in-sql-server"></a>Altre informazioni sulla clausola FOR JSON e sul supporto JSON integrato in SQL Server  
 [Post di blog di Jovan Popovic, Microsoft Program Manager](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Use FOR JSON output in SQL Server and in client apps &#40;SQL Server&#41; (Usare l'output FOR JSON in SQL Server e nelle app client &#40;SQL Server&#41;)](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

