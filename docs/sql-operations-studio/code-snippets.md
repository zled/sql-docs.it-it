---
title: Creare frammenti di codice in Studio operazioni SQL (anteprima) | Documenti Microsoft
description: Informazioni su come creare e usare i frammenti di codice SQL in Studio operazioni SQL (anteprima)
ms.custom: tools|sos
ms.date: 11/15/2017
ms.reviewer: alayu; erickang; sstein
ms.prod: sql-non-specified
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4670c824b1e52776c3d81d097beeb4ccd9e62e2d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>Creare e usare i frammenti di codice per creare rapidamente script Transact-SQL (T-SQL)[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Frammenti di codice [!INCLUDE[name-sos](../includes/name-sos-short.md)] sono modelli che rendono più semplice per creano database e oggetti di database. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)]fornisce diversi frammenti di T-SQL che aiutino a generare rapidamente la sintassi corretta. 

Sono anche possibile creare frammenti di codice definito dall'utente.

## <a name="using-built-in-t-sql-code-snippets"></a>Utilizzo di frammenti di codice T-SQL incorporati

1. Per visualizzare i frammenti di codice disponibili, digitare *sql* nell'editor di query per aprire l'elenco:

   ![frammenti](media/code-snippets/sql-snippets.png)

1. Selezionare il frammento di codice che si desidera utilizzare e genera lo script T-SQL. Ad esempio, selezionare *sqlCreateTable*:

   ![tabella di frammenti](media/code-snippets/create-table.png)

1. Aggiornare i campi evidenziati con i valori specifici. Ad esempio, sostituire *TableName* e *Schema* con i valori per il database:

   ![Sostituire il campo di modello](media/code-snippets/table-from-snippet.png)

   Se il campo che si desidera modificare non è evidenziato (questo avviene quando si sposta il cursore nell'Editor), fare doppio clic sulla parola che si desidera modificare, quindi scegliere **modificare tutte le occorrenze**:

   ![Sostituire il campo di modello](media/code-snippets/change-all.png)

1. Aggiornare o aggiungere eventuali ulteriori T-SQL è necessario per il frammento di codice selezionato. Ad esempio, aggiornare *Column1*, *Column2*e aggiungere altre colonne.


 
## <a name="creating-sql-code-snippets"></a>Creazione di frammenti di codice SQL 

È possibile definire frammenti personalizzati. Per aprire il file di frammento di codice SQL per la modifica:

1. Aprire il *comando tavolozza* (**Maiusc + Ctrl + P**) e il tipo *cattura*e selezionare **preferenze: Apri frammenti di codice utente**:

   ![Sostituire il campo di modello](media/code-snippets/user-snippets.png)

1. Selezionare **SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)]questo articolo illustra in particolare l'utilizzo dei frammenti SQL eredita la funzionalità di frammento di codice da Visual Studio Code. Per ulteriori informazioni, vedere [creare frammenti personalizzati](https://code.visualstudio.com/docs/editor/userdefinedsnippets) nella documentazione di Visual Studio Code. 

   ![Sostituire il campo di modello](media/code-snippets/select-sql.png)

1. Incollare il codice seguente nel *sql.json*:

   ```sql
   "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "   $1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "   Column1 [NVARCHAR](50) NOT NULL,",
    "   Column2 [NVARCHAR](50) NOT NULL",
    "   -- specify more columns here",
    ");",
    "GO"
    ],
   "description": "User-defined snippet example 2"
   }
   ```

1. Salvare il file sql.json.
1. Aprire una nuova finestra editor di query, fare clic su **Ctrl + N**.
2. Tipo **sql**, visualizzare i frammenti di codice di due utente appena aggiunto; *sqlCreateTable2* e *sqlSelectTop5*.

Selezionare uno dei nuovi frammenti di codice e assegnargli un'esecuzione dei test.


## <a name="additional-resources"></a>Risorse aggiuntive

Per informazioni sull'editor SQL, vedere [esercitazione editor di codice](tutorial-sql-editor.md).