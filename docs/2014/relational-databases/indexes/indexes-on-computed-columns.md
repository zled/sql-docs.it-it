---
title: Indici per le colonne calcolate | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9b7d9b25ccb9404011c459ba0275f2ba0c63746a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065587"
---
# <a name="indexes-on-computed-columns"></a>Indici per le colonne calcolate
  È possibile definire gli indici per le colonne calcolate purché siano soddisfatti i requisiti seguenti:  
  
-   Requisiti di proprietà  
  
-   Requisiti di determinismo  
  
-   Requisiti di precisione  
  
-   Requisiti del tipo di dati  
  
-   Requisiti dell'opzione SET  
  
 **Ownership Requirements**  
  
 Tutti i riferimenti a funzioni nella colonna calcolata devono avere lo stesso proprietario della tabella.  
  
 **Determinism Requirements**  
  
> [!IMPORTANT]  
>  Le espressioni sono deterministiche se restituiscono sempre lo stesso risultato per un determinato set di input. La proprietà **IsDeterministic** della funzione [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) indica se una *computed_column_expression* è deterministica.  
  
 La *computed_column_expression* deve essere deterministica. Una *computed_column_expression* è deterministica quando viene soddisfatta una o più delle condizioni seguenti:  
  
-   Tutte le funzioni alle quali l'espressione fa riferimento sono deterministiche e precise. Queste funzioni includono funzioni definite dall'utente e funzioni predefinite. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../user-defined-functions/deterministic-and-nondeterministic-functions.md). Le funzioni potrebbero non essere precise se la colonna calcolata è PERSISTED. Per altre informazioni, vedere [Creazione di indici per colonne calcolate persistenti](#BKMK_persisted) più avanti in questo argomento.  
  
-   Tutte le colonne alle quali viene fatto riferimento nell'espressione appartengono alla tabella contenente la colonna calcolata.  
  
-   Nessun riferimento a una colonna estrae dati da più righe. Ad esempio, funzioni di aggregazione quali SUM o AVG dipendono dai dati presenti in più righe e renderebbero non deterministica una *computed_column_expression* .  
  
-   L'espressione *computed_column_expression* è priva di accesso ai dati di sistema o ai dati utente.  
  
 Qualsiasi colonna calcolata contenente un'espressione CLR (Common Language Runtime) deve essere deterministica e contrassegnata come PERSISTED prima di poter essere indicizzata. Le espressioni di tipo CLR definito dall'utente sono consentite nelle definizioni delle colonne calcolate. Le colonne calcolate di tipo CLR definito dall'utente possono essere indicizzate purché il tipo sia confrontabile. Per altre informazioni, vedere [Tipi CLR definiti dall'utente](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
> [!NOTE]  
>  Quando si fa riferimento ai valori letterali stringa del tipo di dati relativo alla data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si consiglia di convertire in modo esplicito il valore letterale nel tipo di data che si desidera utilizzando uno stile di formato di data deterministico. Per un elenco degli stili del formato di data deterministici, vedere [CAST e CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql). Le espressioni che prevedono la conversione implicita delle stringhe di carattere nei tipi di dati relativi alla data vengono considerate non deterministiche, a meno che il livello di compatibilità del database non venga impostato su 80 o su un valore inferiore. Ciò è dovuto al fatto che i risultati dipendono dalle impostazioni [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) e [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) della sessione del server. I risultati dell'espressione `CONVERT (datetime, '30 listopad 1996', 113)` dipendono ad esempio dall'impostazione LANGUAGE, in quanto la stringa '`30 listopad 1996`' indica mesi diversi in diverse lingue. Analogamente, nell'espressione `DATEADD(mm,3,'2000-12-01')`, [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interpreta la stringa `'2000-12-01'` in base all'impostazione DATEFORMAT.  
>   
>  Anche la conversione implicita dei dati di tipo carattere non Unicode tra regole di confronto viene considerata non deterministica, a meno che il livello di compatibilità non sia impostato su un valore minore o uguale a 80.  
>   
>  Se l'impostazione del livello di compatibilità del database è 90, non è possibile creare indici su colonne calcolate contenenti tali espressioni. Tuttavia, le colonne calcolate esistenti che includono queste espressioni da un database aggiornato sono gestibili. Se si utilizzano colonne calcolate che includono conversioni implicite da valori di tipo stringa a valori di tipo data, verificare che le impostazioni LANGUAGE e DATEFORMAT siano consistenti nei database e nelle applicazioni per evitare l'eventuale danneggiamento dell'indice.  
  
 **Precision Requirements**  
  
 La *computed_column_expression* deve essere precisa. Una *computed_column_expression* è precisa quando viene soddisfatta una o più delle condizioni seguenti:  
  
-   Non è un'espressione dei tipi di dati `float` o `real`.  
  
-   Non usa un `float` o `real` tipo di dati nella relativa definizione. Ad esempio, nell'istruzione seguente, colonna `y` è `int` ed deterministica, ma non precisa.  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  Qualsiasi `float` oppure `real` espressione sono considerata non precisa e non può essere una chiave di un indice; `float` o `real` espressione può essere utilizzata in una vista indicizzata, ma non come una chiave. Questa considerazione è valida anche per le colonne calcolate. Qualsiasi funzione, espressione o funzione definita dall'utente è considerata non precisa se includono `float` o `real` espressioni. Sono comprese le espressioni logiche (confronti).  
  
 La proprietà **IsPrecise** della funzione COLUMNPROPERTY indica se una *computed_column_expression* è precisa.  
  
 **Data Type Requirements**  
  
-   Il *computed_column_expression* definita per la colonna calcolata non può restituire il `text`, `ntext`, o `image` tipi di dati.  
  
-   Le colonne calcolate derivate da `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, e `xml` tipi di dati possono essere indicizzati, purché il tipo di dati di colonna calcolata sia consentito come colonna chiave di indice.  
  
-   Le colonne calcolate derivate da `image`, `ntext`, e `text` tipi di dati possono essere colonne non chiave (incluse) in un indice non cluster, purché il tipo di dati di colonna calcolata sia consentito come colonna non chiave dell'indice.  
  
 **SET Option Requirements**  
  
-   Quando viene eseguita l'istruzione CREATE TABLE o ALTER TABLE che definisce la colonna calcolata, è necessario impostare su ON l'opzione a livello di connessione ANSI_NULL. La funzione [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) indica se l'opzione è impostata su ON nella proprietà **IsAnsiNullsOn** .  
  
-   Per la connessione in corrispondenza della quale viene creato l'indice e per tutte le connessioni che tentano di eseguire istruzioni INSERT, UPDATE o DELETE che modificano i valori dell'indice, sei opzioni SET devono essere impostate su ON e un'opzione SET deve essere impostata su OFF. Per tutte le eventuali istruzioni SELECT eseguite da una connessione per la quale non sono state definite esattamente le impostazioni delle opzioni indicate di seguito, Query Optimizer ignora gli indici definiti su una colonna calcolata.  
  
    -   L'opzione NUMERIC_ROUNDABORT deve essere impostata su OFF e le opzioni seguenti su ON.  
  
    -   ANSI_NULLS  
  
    -   ANSI_PADDING  
  
    -   ANSI_WARNINGS  
  
    -   ARITHABORT  
  
    -   CONCAT_NULL_YIELDS_NULL  
  
    -   QUOTED_IDENTIFIER  
  
     Quando il livello di compatibilità del database è impostato su 90 o su un valore maggiore, l'impostazione di ANSI_WARNINGS su ON comporta anche l'impostazione implicita di ARITHABORT su ON.  
  
##  <a name="BKMK_persisted"></a> Creazione di indici per colonne calcolate persistenti  
 È possibile creare un indice su una colonna calcolata. definita da un'espressione deterministica, ma non precisa, se la colonna è contrassegnata come PERSISTED nell'istruzione CREATE TABLE oppure ALTER TABLE. Ciò significa che il [!INCLUDE[ssDE](../../../includes/ssde-md.md)] utilizza questi valori persistenti quando viene creato un indice sulla colonna e quando l'indice viene fatto riferimento in una query. Questa opzione consente di creare un indice su una colonna calcolata quando [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)], sia deterministica e precisa.  
  
## <a name="related-content"></a>Contenuto correlato  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
