---
title: Architettura di Graph SQL | Documenti Microsoft
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: graphs
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4ca6de15012a8fb929c207ab1a79a41607bd74cc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sql-graph-architecture"></a>Architettura di Graph SQL  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Informazioni su come grafico SQL è progettato. Conoscere le nozioni di base renderà più facile da comprendere altri articoli grafico SQL.
 
## <a name="sql-graph-database"></a>Database SQL di Graph
Gli utenti possono creare un grafico per ogni database. Un grafico è una raccolta di tabelle di nodo e bordo. Bordo o nodo tabelle possono essere create in qualsiasi schema nel database, ma appartengono a un grafo logico. Una tabella di nodo è una raccolta di tipo simile di nodi. Ad esempio, una tabella di persona nodo contiene tutti i nodi di persona appartenenti a un grafico. Analogamente, una tabella edge è una raccolta di tipo simile di bordi. Ad esempio, una tabella edge amici contiene tutti i bordi che si connettono a un utente a un altro utente. Poiché i nodi e bordi vengono archiviati in tabelle, la maggior parte delle operazioni supportate per le tabelle regolari sono supportata nelle tabelle di nodo o bordo. 
 
 
![architettura di graph SQL](../../relational-databases/graphs/media/sql-graph-architecture.png "architettura del database Sql grafico")   

Figura 1: Architettura del database SQL grafico
 
## <a name="node-table"></a>Tabella del nodo
Una tabella di nodo rappresenta un'entità in uno schema di grafico. Ogni volta che nodo viene creata una tabella, insieme a colonne definite dall'utente, implicita `$node_id` creazione della colonna, che identifica in modo univoco un nodo specifico nel database. I valori in `$node_id` vengono generate automaticamente e sono una combinazione di `object_id` di tale tabella del nodo e un valore bigint generato internamente. Tuttavia, quando il `$node_id` colonna è selezionata, viene visualizzato un valore calcolato sotto forma di una stringa JSON. Inoltre, `$node_id` è una pseudo colonna, che esegue il mapping a un nome interno con una stringa esadecimale in essa contenuti. Quando si seleziona `$node_id` dalla tabella, verrà visualizzato il nome della colonna come `$node_id_<hex_string>`. Utilizzo di nomi di pseudo-colonna nelle query è lo strumento consigliato per l'esecuzione di query interno `$node_id` colonna e con nome interno a stringa esadecimale deve essere evitati.

È consigliabile che gli utenti creano un vincolo unique o indice di `$node_id` colonna al momento della creazione della tabella di nodo, ma se non ne è creato, un valore predefinito di indice non cluster univoco viene creato automaticamente. Tuttavia, qualsiasi indice su una pseudo colonna del grafico viene creato nelle colonne interne sottostante. Ovvero, un indice creato per il `$node_id` colonna, verrà visualizzata a interno `graph_id_<hex_string>` colonna.   


## <a name="edge-table"></a>Tabella Edge
Una tabella edge rappresenta una relazione in un grafico. Bordi vengano sempre indirizzati e connettono a due nodi. Una tabella edge consente agli utenti di modellare relazioni molti-a-molti nel grafico. Una tabella edge può non avere attributi definiti dall'utente in essa contenuti o. Ogni volta che viene creata una tabella edge, con gli attributi definiti dall'utente, vengono create tre colonne implicite della tabella edge:

|Nome colonna    |Description  |
|---   |---  |
|`$edge_id`   |Identifica in modo univoco un bordo specificato nel database. È una colonna generata e il valore è una combinazione di object_id della tabella edge e un valore bigint generato internamente. Tuttavia, quando il `$edge_id` colonna è selezionata, viene visualizzato un valore calcolato sotto forma di una stringa JSON. `$edge_id`è una pseudo colonna, che esegue il mapping a un nome interno con una stringa esadecimale in essa contenuti. Quando si seleziona `$edge_id` dalla tabella, verrà visualizzato il nome della colonna come `$edge_id_\<hex_string>`. Utilizzo di nomi di pseudo-colonna nelle query è lo strumento consigliato per l'esecuzione di query interno `$edge_id` colonna e con nome interno a stringa esadecimale deve essere evitati. |
|`$from_id`   |Archivia il `$node_id` del nodo, da cui ha origine il bordo.  |
|`$to_id`   |Archivia il `$node_id` del nodo, in cui termina il bordo. |

I nodi che è possibile connettere un bordo specificato non sia disciplinato da dati inseriti nel `$from_id` e `$to_id` colonne. Nella prima versione, non è possibile definire vincoli sulla tabella edge, per applicare restrizioni di connettersi a qualsiasi tipo di due dei nodi. Ovvero, un bordo può connettersi due nodi nel grafico, indipendentemente dal loro tipi.

Simile al `$node_id` colonna, è consigliabile che gli utenti creare un vincolo o un indice univoco sul `$edge_id` colonna al momento della creazione della tabella edge, ma se uno non è creata, indice non cluster univoco viene creato automaticamente sul valore predefinito è Questa colonna. Tuttavia, qualsiasi indice su una pseudo colonna del grafico viene creato nelle colonne interne sottostante. Ovvero, un indice creato per il `$edge_id` colonna, verrà visualizzata a interno `graph_id_<hex_string>` colonna. È inoltre consigliabile, per gli scenari OLTP, che gli utenti di creare un indice su (`$from_id`, `$to_id`) le colonne, per le ricerche più veloci nella direzione del bordo.  

Figura 2 mostra come nodo e bordo tabelle vengono archiviate nel database. 

![tabelle di amici persona](../../relational-databases/graphs/media/person-friends-tables.png "nodo persona e amici bordo tabelle")   

Figura 2: Rappresentazione nodo e bordo tabella



## <a name="metadata"></a>Metadati
Utilizzare queste viste per i metadati per visualizzare gli attributi di un bordo o nodo di tabella.
 
### <a name="systables"></a>sys.tables
Tipo, bit seguenti sono nuovi, verranno aggiunte colonne di SYS. TABELLE. Se `is_node` è impostato su 1, che indica che la tabella è un nodo e, se `is_edge` è impostato su 1, che indica che la tabella è una tabella edge.
 
|Nome colonna |Tipo di dati |Description |
|--- |---|--- |
|is_node |bit |1 = si tratta di un nodo di tabella |
|is_edge |bit |1 = si tratta di una tabella edge |
 
### <a name="syscolumns"></a>sys.columns
Il `sys.columns` vista contiene colonne aggiuntive `graph_type` e `graph_type_desc`, che indicano il tipo di colonna nelle tabelle di nodo e bordo.
 
|Nome colonna |Tipo di dati |Description |
|--- |---|--- |
|graph_type |int |Colonna interna con un set di valori. I valori sono compresi tra 1-8 per le colonne di grafico e NULL per gli altri utenti.  |
|graph_type_desc |nvarchar(60)  |colonna interna con un set di valori |
 
Nella tabella seguente sono elencati i valori validi per `graph_type` colonna

|Valore della colonna  |Description  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns`inoltre archiviate informazioni sulle colonne implicite create nelle tabelle di nodo o bordo. Le seguenti informazioni possono essere recuperate da Sys. Columns, tuttavia, gli utenti non è possibile selezionare queste colonne da una tabella di nodo o bordo. 

Colonne implicite in una tabella di nodo  
|Nome colonna    |Tipo di dati  |is_hidden  |Commento  |
|---  |---|---|---  |
|graph_id_\<hex_string > |bigint |1  |colonna graph_id interno  |
|$node_id_\<hex_string > |NVARCHAR   |0  |Colonna di id di nodo esterno  |

Colonne implicite in una tabella edge  
|Nome colonna    |Tipo di dati  |is_hidden  |Commento  |
|---  |---|---|---  |
|graph_id_\<hex_string > |bigint |1  |colonna graph_id interno  |
|$edge_id_\<hex_string > |NVARCHAR   |0  |colonna di id lato esterno  |
|from_obj_id_\<hex_string >  |INT    |1  |interno dall'oggetto con id nodo  |
|from_id_\<hex_string >  |bigint |1  |Interno dal nodo graph_id  |
|$from_id_\<hex_string > |NVARCHAR   |0  |esterno dall'id di nodo  |
|to_obj_id_\<hex_string >    |INT    |1  |id oggetto del nodo interno  |
|to_id_\<hex_string >    |bigint |1  |Il nodo graph_id  |
|$to_id_\<hex_string >   |NVARCHAR   |0  |all'id di nodo esterno  |
 
### <a name="system-functions"></a>Funzioni di sistema
Le funzioni predefinite seguenti vengono aggiunti. Questi consente agli utenti di estrarre informazioni da colonne generate. Si noti che, questi metodi non convaliderà l'input dell'utente. Se l'utente specifica un oggetto non valido `sys.node_id` il metodo estrarre la parte appropriata e restituirlo. Ad esempio, si avranno OBJECT_ID_FROM_NODE_ID un `$node_id` come input e restituiscono object_id della tabella, il nodo appartiene. 
 
|Predefinito   |Description  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |Estrarre object_id da un node_id  |
|GRAPH_ID_FROM_NODE_ID  |Estrarre il graph_id da un node_id  |
|NODE_ID_FROM_PARTS |Costruire un node_id da un object_id e un graph_id  |
|OBJECT_ID_FROM_EDGE_ID |Estrarre object_id da edge_id  |
|GRAPH_ID_FROM_EDGE_ID  |Estrarre l'identità da edge_id  |
|EDGE_ID_FROM_PARTS |Costruire edge_id da object_id e identità  |



## <a name="transact-sql-reference"></a>Riferimento a Transact-SQL 
Informazioni di [!INCLUDE[tsql-md](../../includes/tsql-md.md)] estensioni introdotte in SQL Server e Database SQL di Azure, che consentono la creazione e l'esecuzione di query gli oggetti del grafico. Le estensioni del linguaggio di query consentono di query e attraversare il grafico utilizzando la sintassi di art ASCII.
 
### <a name="data-definition-language-ddl-statements"></a>Istruzioni di Data Definition Language (DDL)
|Attività   |Argomento correlato  |Note
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE `è ora esteso per supportare la creazione di una tabella come nodo o un bordo AS. Si noti che una tabella edge può o può non avere eventuali attributi definiti dall'utente.  |
|ALTER TABLE    |[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|È possibile modificare le tabelle di nodo e bordo nello stesso modo, viene usato una tabella relazionale di `ALTER TABLE`. Gli utenti possono aggiungere o modificare le colonne definite dall'utente, gli indici o vincoli. Tuttavia, la modifica di colonne interno grafico, come `$node_id` o `$edge_id`, si verificherà un errore.  |
|CREATE INDEX   |[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  |Gli utenti possono creare indici in pseudo- colonne e le colonne definite dall'utente nelle tabelle di nodo e bordo. Sono supportati tutti i tipi di indice, inclusi gli indici columnstore cluster e non cluster.  |
|DROP TABLE |[DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)  |È possibile eliminare le tabelle di nodo e bordo esattamente una tabella relazionale, utilizza il `DROP TABLE`. Tuttavia, in questa versione, non sono presenti vincoli per garantire che nessun bordi puntare a un nodo eliminato e sottomenu l'eliminazione dei bordi, in seguito all'eliminazione di un nodo o una tabella del nodo non è supportata. È consigliabile se viene eliminata una tabella di nodo, gli utenti eliminare tutti i bordi connessi ai nodi di tale tabella nodo manualmente per mantenere l'integrità del grafico.  |


### <a name="data-manipulation-language-dml-statements"></a>Istruzioni di Data Manipulation Language (DML)
|Attività   |Argomento correlato  |Note
|---  |---  |---  |
|INSERT |[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)|Inserimento in una tabella di nodo è alcuna differenza rispetto all'inserimento in una tabella relazionale. I valori per `$node_id` colonna viene generata automaticamente. Tentativo di inserire un valore in `$node_id` o `$edge_id` colonna verrà generato un errore. Gli utenti devono fornire valori per `$from_id` e `$to_id` colonne durante l'inserimento in una tabella edge. `$from_id`e `$to_id` sono il `$node_id` valori dei nodi che si connette un bordo specificato.  |
|DELETE | [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|Come verrà eliminata dalle tabelle relazionali, è possono eliminare dati dalle tabelle bordo o nodo nello stesso modo. Tuttavia, in questa versione, non sono presenti vincoli per garantire che nessun bordi puntare a un nodo eliminato e sottomenu l'eliminazione dei bordi, in seguito all'eliminazione di un nodo non è supportata. È consigliabile che ogni volta che viene eliminato un nodo, tutti i bordi di connessi a tale nodo vengono eliminati anche, per mantenere l'integrità del grafico.  |
|UPDATE |[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  |I valori nelle colonne definite dall'utente possono essere aggiornati usando l'istruzione UPDATE. L'aggiornamento di colonne interno grafico, `$node_id`, `$edge_id`, `$from_id` e `$to_id` non è consentito.  |
|MERGE |[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  |`MERGE`istruzione non è supportata in un nodo o bordo della tabella.  |


### <a name="query-statements"></a>Istruzioni di query
|Attività   |Argomento correlato  |Note
|---  |---  |---  |
|SELECT |[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|I nodi e bordi vengono archiviati internamente come tabelle, pertanto la maggior parte delle operazioni supportate in una tabella in SQL Server o Database SQL di Azure sono supportata per le tabelle di nodo e bordo  |
|MATCH  | [CORRISPONDENZA &#40; Transact-SQL &#41;](../../t-sql/queries/match-sql-graph.md)|Predefinite di corrispondenza sono stato introdotto per supportare i criteri di ricerca e l'attraversamento tramite graph.  |



## <a name="limitations-and-known-issues"></a>Limitazioni e problemi noti  
Esistono alcune limitazioni sulle tabelle di nodo e bordo in questa versione:
* Tabelle temporanee globali o locali non possono essere bordo o nodo tabelle.
* Impossibile dichiarare le variabili di tabella e tipi di tabella come tabella bordo o di nodo. 
* Nodo e bordo tabelle non possono essere create come tabelle temporali con controllo delle versioni del sistema.   
* Le tabelle di nodo e bordo non possono essere ottimizzata per la memoria.  
* Gli utenti non è possibile aggiornare le colonne to_id $ di un bordo utilizzando l'istruzione UPDATE from_id $. Per aggiornare i nodi che si connette un bordo, gli utenti avranno inserire il nuovo bordo che punta a nuovi nodi ed eliminare quello precedente.
* Le query su oggetti grafico non sono supportate tra database. 


## <a name="next-steps"></a>Passaggi successivi
Per iniziare con la nuova sintassi, vedere [SQL grafico Database - esempio](./sql-graph-sample.md)
 

