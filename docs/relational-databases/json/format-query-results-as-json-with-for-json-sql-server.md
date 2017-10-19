---
title: Formattare i risultati delle query in formato JSON con FOR JSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/18/2017
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
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 8ee99c52515908e93a44e936504fd8ccbd74793f
ms.contentlocale: it-it
ms.lasthandoff: 10/13/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Formattare i risultati delle query in formato JSON con FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

È possibile formattare i risultati delle query come JSON o esportare i dati da SQL Server in formato JSON aggiungendo la clausola **FOR JSON** a un'istruzione **SELECT** . Usare la clausola **FOR JSON** per semplificare le applicazioni client delegando la formattazione dell'output JSON dell'app a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
 Quando si usa la clausola **FOR JSON** è possibile specificare la struttura dell'output JSON in modo esplicito o lasciare che l'output sia determinato dalla struttura dell'istruzione SELECT.  
  
-   Usare **FOR JSON PATH** per mantenere il controllo completo sul formato dell'output JSON. È possibile creare oggetti wrapper e annidare proprietà complesse.  
  
-   Usare **FOR JSON AUTO** per formattare l'output JSON automaticamente in base alla struttura dell'istruzione SELECT.  
  
Di seguito è riportato un esempio di istruzione **SELECT** con la clausola **FOR JSON** e il relativo output.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png)
  
## <a name="option-1---you-control-output-with-for-json-path"></a>Opzione 1: controllo dell'output con FOR JSON PATH
In modalità **PATH** è possibile formattare l'output annidato usando la sintassi con il punto, ad esempio `'Item.Price'` .  

Ecco una query di esempio che usa la modalità **PATH** con la clausola **FOR JSON** . L'esempio seguente usa anche l'opzione **ROOT** per specificare un elemento radice denominato. 
  
 ![Diagramma di flusso dell'output FOR JSON](../../relational-databases/json/media/forjson-example1.png) 

### <a name="more-info-about-for-json-path"></a>Altre informazioni su FOR JSON PATH
Per informazioni dettagliate ed esempi, vedere [Formattare l'output JSON annidato con la modalità PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Per la sintassi e l'uso, vedere [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="option-2---select-statement-controls-output-with-for-json-auto"></a>Opzione 2: l'istruzione SELECT controlla l'output con FOR JSON AUTO
In modalità **AUTO** il formato dell'output JSON è determinato dalla struttura dell'istruzione SELECT.

Per impostazione predefinita, i valori **null** non vengono inclusi nell'output. È possibile usare **INCLUDE_NULL_VALUES** per modificare questo comportamento.  

Ecco una query di esempio che usa la modalità **AUTO** con la clausola **FOR JSON** .
 
**Query:**  
  
```sql  
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
 
### <a name="more-info-about-for-json-auto"></a>Altre informazioni su FOR JSON AUTO
Per informazioni dettagliate ed esempi, vedere [Formattare automaticamente l'output JSON con la modalità AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Per la sintassi e l'uso, vedere [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Controllare altre opzioni di output JSON  
Per controllare l'output della clausola **FOR JSON** è possibile usare le seguenti opzioni aggiuntive.  
  
-   **ROOT**. Per aggiungere un unico elemento di primo livello all'output JSON, specificare l'opzione **ROOT** . Se non si specifica questa opzione, l'output JSON non ha alcun elemento radice. Per altre informazioni, vedere [Add a Root Node to JSON Output with the ROOT Option &#40;SQL Server&#41; (Aggiungere un nodo radice all'output JSON con l'opzione ROOT &#40;SQL Server&#41;)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   **INCLUDE_NULL_VALUES**. Per includere valori Null nell'output JSON, specificare l'opzione **INCLUDE_NULL_VALUES** . Se non si specifica questa opzione, l'output non include le proprietà JSON per i valori NULL presenti nei risultati della query. Per altre informazioni, vedere [Includere valori in JSON - Opzione INCLUDE_NULL_VALUES](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   **WITHOUT_ARRAY_WRAPPER**. Per rimuovere le parentesi quadre che racchiudono l'output JSON della clausola **FOR JSON** per impostazione predefinita, specificare l'opzione **WITHOUT_ARRAY_WRAPPER** . Usare questa opzione per generare un singolo oggetto JSON come output da un risultato a riga singola. Se non si specifica questa opzione, l'output JSON viene formattato come una matrice, ovvero è racchiuso tra parentesi quadre. Per altre informazioni, vedere [Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option &#40;SQL Server&#41; (Rimuovere le parentesi quadre dall'output JSON con l'opzione WITHOUT_ARRAY_WRAPPER &#40;SQL Server&#41;)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Output della clausola FOR JSON  
L'output della clausola **FOR JSON** ha le caratteristiche seguenti:  
  
1.  Il set di risultati contiene un'unica colonna.
    -   Un set di risultati di piccole dimensioni può contenere un'unica riga.
    -   Un set di risultati di grandi dimensioni suddivide la stringa JSON su più righe.
        -   Per impostazione predefinita, SQL Server Management Studio (SSMS) concatena i risultati in una singola riga quando l'impostazione dell'output è **Risultati in formato griglia**. La barra di stato di SQL Server Management Studio visualizza il conteggio effettivo delle righe.
        -   Altre applicazioni client possono richiedere codice per ricombinare i risultati eccessivamente lunghi in un'unica stringa JSON valida concatenando i contenuti di più righe. Per un esempio di questo codice in un'applicazione C#, vedere [Usare l'output FOR JSON in un'app client C#](https://docs.microsoft.com/en-us/sql/relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server#use-for-json-output-in-a-c-client-app).
  
     ![Esempio di output FOR JSON](../../relational-databases/json/media/forjson-example2.png)  
  
2.  I risultati vengono formattati sotto forma di matrice di oggetti JSON.  
  
    -   Il numero di elementi nella matrice JSON è uguale al numero di righe nei risultati dell'istruzione SELECT (prima che venga applicata la clausola FOR JSON). 
  
    -   Ogni riga nei risultati dell'istruzione SELECT (prima che venga applicata la clausola FOR JSON) diventa un oggetto JSON separato nella matrice.  
  
    -   Ogni colonna nei risultati dell'istruzione SELECT (prima che venga applicata la clausola FOR JSON) diventa una proprietà dell'oggetto JSON.  
  
3.  I nomi delle colonne e i valori corrispondenti vengono sottoposti a escape in base alla sintassi JSON. Per altre informazioni, vedere [How FOR JSON escapes special characters and control characters &#40;SQL Server&#41; (Sequenze di escape FOR JSON per i caratteri speciali e di controllo &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).
  
### <a name="example"></a>Esempio
Ecco un esempio che illustra come la clausola **FOR JSON** formatta l'output JSON.  
  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.
  
## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Use FOR JSON output in SQL Server and in client apps &#40;SQL Server&#41; (Usare l'output FOR JSON in SQL Server e nelle app client &#40;SQL Server&#41;)](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

