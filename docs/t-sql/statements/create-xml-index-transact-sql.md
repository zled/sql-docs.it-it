---
title: CREARE l'indice XML (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- XML_TSQL
- CREATE_XML_INDEX_TSQL
- XML INDEX
- CREATE_XML_TSQL
- XML
- CREATE XML
- CREATE XML INDEX
- XML_INDEX_TSQL
- FOR_XML_TSQL
dev_langs: TSQL
helpviewer_keywords:
- CREATE XML INDEX statement
- CREATE INDEX statement
- index creation [SQL Server], XML indexes
- XML indexes [SQL Server], creating
ms.assetid: c510cfbc-68be-4736-b3cc-dc5b7aa51f14
caps.latest.revision: "38"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 28de81b28ee31c172d1a31644f6847579af4e961
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-xml-index-transact-sql"></a>CREATE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un indice XML in una tabella specificata. L'indice può essere creato prima dell'immissione dei dati nella tabella. È possibile creare indici XML per tabelle di un altro database specificando un nome di database completo.  
  
> [!NOTE]  
>  Per creare un indice relazionale, vedere [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md). Per informazioni su come creare un indice spaziale, vedere [CREATE SPATIAL INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-spatial-index-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Create XML Index   
CREATE [ PRIMARY ] XML INDEX index_name   
    ON <object> ( xml_column_name )  
    [ USING XML INDEX xml_index_name   
        [ FOR { VALUE | PATH | PROPERTY } ] ]  
    [ WITH ( <xml_index_option> [ ,...n ] ) ]  
[ ; ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_name  
}  
  
<xml_index_option> ::=  
{   
    PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [PRIMARY] XML  
 Crea un indice XML su specificato **xml** colonna. Quando viene specificata la parola chiave PRIMARY, viene creato un indice cluster con una chiave cluster costituita dalla chiave di clustering della tabella utente e da un identificatore di nodo XML. Per ogni tabella è possibile creare al massimo 249 indici XML. Quando si crea un indice XML, è necessario tenere presente quanto segue:  
  
-   È necessario che esista un indice cluster sulla chiave primaria della tabella utente.  
  
-   La chiave di clustering della tabella utente può includere al massimo 15 colonne.  
  
-   Ogni **xml** colonna in una tabella può includere un indice XML primario e più indici XML secondari.  
  
-   Un indice XML primario in un **xml** colonna deve essere presente prima di poter creare un indice XML secondario sulla colonna.  
  
-   Un indice XML può essere creato solo in una singola **xml** colonna. Non è possibile creare un indice XML su un non -**xml** colonna, né creare un indice relazionale in un **xml** colonna.  
  
-   È possibile creare un indice XML primario o secondario, scegliere un **xml** colonna in una vista, in una variabile con valori di tabella con **xml** colonne, o **xml** variabili di tipo.  
  
-   Non è possibile creare un indice XML primario in una calcolata **xml** colonna.  
  
-   Le impostazioni delle opzioni SET devono corrispondere a quelle necessarie per le viste indicizzate e gli indici su colonne calcolate. In particolare, deve impostare l'opzione ARITHABORT su ON quando viene creato un indice XML e inserimento, eliminazione o aggiornamento di valori di **xml** colonna.  
  
 Per altre informazioni, vedere [Indici XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
 *index_name*  
 Nome dell'indice. I nomi degli indici devono essere univoci all'interno di una tabella, ma non all'interno di un database. I nomi di indice devono rispettare le regole di [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 I nomi di indice XML primari non possono iniziare con i seguenti caratteri:  **#** ,  **##** ,  **@** , o  **@@**  .  
  
 *xml_column_name*  
 È il **xml** su cui è basato l'indice di colonna. Un solo **xml** colonna può essere specificata in una singola definizione di indice XML; tuttavia, possibile creare più indici XML secondari su un **xml** colonna.  
  
 USING XML INDEX *xml_index_name*  
 Specifica l'indice XML primario da usare per la creazione di un indice XML secondario.  
  
 FOR { VALUE | PATH | PROPERTY }  
 Specifica il tipo di indice XML secondario.  
  
 Value  
 Crea un indice XML secondario su colonne con le colonne chiave (valore di nodo e percorso) dell'indice XML primario.  
  
 PATH  
 Crea un indice XML secondario su colonne compilate in base ai valori di percorso e i valori di nodo dell'indice XML primario. Nell'indice secondario PATH i valori di nodo e di percorso sono colonne chiave che consentono di eseguire le ricerche dei percorsi in modo più efficiente.  
  
 PROPERTY  
 Crea un indice XML secondario su colonne (valore di chiave primaria, percorso e nodo) dell'indice XML primario, dove il valore di chiave primaria è la chiave primaria della tabella di base.  
  
 **\<Oggetto >:: =**  
  
 Oggetto con nome completo o non completo che si desidera indicizzare.  
  
 *database_name*  
 Nome del database.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella.  
  
 *table_name*  
 Nome della tabella da indicizzare.  
  
 **\<xml_index_option >:: =** 
  
 Specifica le opzioni da usare quando si crea l'indice.  
  
 PAD_INDEX  **=**  {ON | **OFF** }  
 Specifica il riempimento dell'indice. Il valore predefinito è OFF.  
  
 ON  
 La percentuale di spazio libero specificata dal *fillfactor* viene applicata alle pagine di livello intermedio dell'indice.  
  
 DISATTIVARE o *fillfactor* non è specificato  
 Le pagine di livello intermedio vengono riempite poco al di sotto della capacità massima, in modo che lo spazio residuo sia sufficiente per almeno una riga della dimensione massima supportata dall'indice, in base al set di chiavi nelle pagine intermedie.  
  
 L'opzione PAD_INDEX risulta utile solo quando si specifica FILLFACTOR, in quanto PAD_INDEX usano la percentuale specificata in FILLFACTOR. Se la percentuale specificata in FILLFACTOR non consente l'inserimento di una riga, [!INCLUDE[ssDE](../../includes/ssde-md.md)] sostituisce internamente tale percentuale in modo da rendere disponibile lo spazio minimo necessario. Il numero di righe in una pagina di indice intermedio non è mai inferiore a due, indipendentemente dal valore di *fillfactor*.  
  
 Fattore di riempimento  **=**  *fattore di riempimento*  
 Specifica una percentuale che indica il livello di riempimento del livello foglia di ogni pagina di indice applicato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o la ricompilazione dell'indice. *fattore di riempimento* deve essere un valore intero compreso tra 1 e 100. Il valore predefinito è 0. Se *fillfactor* è 100 o 0, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono creati indici con pagine foglia riempite fino alla capacità.  
  
> [!NOTE]  
>  I valori 0 e 100 relativi al fattore di riempimento sono equivalenti.  
  
 L'impostazione di FILLFACTOR viene applicata solo in fase di creazione o di ricompilazione dell'indice. La percentuale specificata di spazio vuoto delle pagine non viene mantenuta in modo dinamico da [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Per visualizzare l'impostazione del fattore di riempimento, utilizzare il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo.  
  
> [!IMPORTANT]  
>  La creazione di un indice cluster con un valore FILLFACTOR minore di 100 influisce sulla quantità di spazio di archiviazione occupata dai dati perché i dati vengono ridistribuiti da [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione dell'indice cluster.  
  
 Per altre informazioni, vedere [Specificare un fattore di riempimento per un indice](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 L'OPZIONE SORT_IN_TEMPDB  **=**  {ON | **OFF** }  
 Specifica se archiviare risultati temporanei dell'ordinamento in **tempdb**. Il valore predefinito è OFF.  
  
 ON  
 I risultati intermedi dell'ordinamento utilizzati per compilare l'indice vengono archiviati **tempdb**. Questo potrebbe ridurre il tempo necessario per creare un indice se **tempdb** si trova in un set di dischi diverso rispetto al database utente. La quantità di spazio su disco utilizzata durante la compilazione dell'indice sarà tuttavia maggiore.  
  
 OFF  
 I risultati intermedi dell'ordinamento vengono archiviati nello stesso database dell'indice.  
  
 Oltre allo spazio necessario nel database utente per creare l'indice, **tempdb** deve essere disponibile la stessa quantità di spazio aggiuntivo per archiviare i risultati intermedi dell'ordinamento. Per ulteriori informazioni, vedere [opzione SORT_IN_TEMPDB per indici](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md).  
  
 IGNORE_DUP_KEY **= OFF**  
 Non ha effetto per gli indici XML perché il tipo di indice non è mai univoco. Non impostare questa opzione su ON. In caso contrario, viene generato un errore.  
  
 DROP_EXISTING  **=**  {ON | **OFF** }  
 Specifica che è necessario eliminare e quindi ricompilare l'indice XML denominato preesistente. Il valore predefinito è OFF.  
  
 ON  
 L'indice esistente deve essere eliminato e ricompilato. Il nome di indice specificato deve corrispondere a quello dell'indice esistente, mentre la definizione dell'indice può essere modificata. È possibile, ad esempio, specificare valori diversi per le colonne, il tipo di ordinamento, lo schema di partizione o le opzioni dell'indice.  
  
 OFF  
 Se il nome di indice specificato esiste già, viene visualizzato un messaggio di errore.  
  
 Il tipo di indice non può essere modificato tramite l'opzione DROP_EXISTING. Non è inoltre possibile ridefinire un indice XML primario come indice XML secondario o viceversa.  
  
 ONLINE **= OFF**  
 Specifica che le tabelle sottostanti e gli indici associati non sono disponibili per le query e la modifica dei dati durante l'operazione sull'indice. In questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le operazioni di compilazione di indici online non sono supportate per gli indici XML. Se questa opzione è impostata su ON per un indice XML, viene generato un errore. Omettere l'opzione ONLINE o impostare ONLINE su OFF.  
  
 Un'operazione offline sull'indice che crea, ricompila o elimina un indice XML acquisisce un blocco di modifica dello schema (SCH-M) per la tabella. Il blocco impedisce agli utenti di accedere alla tabella sottostante per la durata dell'operazione.  
  
> [!NOTE]  
>  Le operazioni sugli indici online sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | OFF}  
 Specifica se sono consentiti blocchi di riga. Il valore predefinito è ON.  
  
 ON  
 I blocchi di riga sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi di riga.  
  
 OFF  
 I blocchi di riga non vengono utilizzati.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | OFF}  
 Specifica se sono consentiti blocchi a livello di pagina. Il valore predefinito è ON.  
  
 ON  
 I blocchi a livello di pagina sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi a livello di pagina.  
  
 OFF  
 I blocchi a livello di pagina non vengono utilizzati.  
  
 MAXDOP  **=**  *max_degree_of_parallelism*  
 Esegue l'override di [il max degree of parallelism opzione di configurazione Server Configurare](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) opzione di configurazione per la durata dell'operazione sull'indice. Utilizzare MAXDOP per limitare il numero di processori utilizzati durante l'esecuzione di un piano parallelo. Il valore massimo è 64 processori.  
  
> [!IMPORTANT]  
>  Sebbene l'opzione MAXDOP sia supportata a livello di sintassi per tutti gli indici XML, per un indice XML primario CREATE XML INDEX usano solo un processore singolo.  
  
 *max_degree_of_parallelism* può essere:  
  
 1  
 Disattiva la generazione di piani paralleli.  
  
 \>1  
 Consente di limitare al valore specificato, o a un valore più basso in base al carico di lavoro corrente del sistema, il numero massimo di processori usati in un'operazione parallela sugli indici.  
  
 0 (predefinito)  
 Utilizza il numero effettivo di processori o un numero inferiore in base al carico di lavoro corrente del sistema.  
  
 Per altre informazioni, vedere [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Operazioni parallele sugli indici non sono disponibili in ogni edizione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="remarks"></a>Osservazioni  
 Le colonne calcolate derivate da **xml** dati tipi possono essere indicizzate come colonna chiave o inclusa non chiave purché il tipo di dati della colonna calcolata sia consentito come colonna chiave dell'indice o colonna non chiave. Non è possibile creare un indice XML primario in una calcolata **xml** colonna.  
  
 Per visualizzare informazioni sugli indici XML, utilizzare il [xml_indexes](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md) vista del catalogo.  
  
 Per ulteriori informazioni sugli indici XML, vedere [indici XML &#40; SQL Server &#41; ](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
## <a name="additional-remarks-on-index-creation"></a>Osservazioni aggiuntive sulla creazione dell'indice  
 Per ulteriori informazioni sulla creazione dell'indice, vedere la sezione "Osservazioni" in [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-primary-xml-index"></a>A. Creazione di un indice XML primario  
 Nell'esempio seguente viene creato un indice XML primario sulla colonna `CatalogDescription` della tabella `Production.ProductModel`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT * FROM sys.indexes  
            WHERE name = N'PXML_ProductModel_CatalogDescription')  
    DROP INDEX PXML_ProductModel_CatalogDescription   
        ON Production.ProductModel;  
GO  
CREATE PRIMARY XML INDEX PXML_ProductModel_CatalogDescription  
    ON Production.ProductModel (CatalogDescription);  
GO  
```  
  
### <a name="b-creating-a-secondary-xml-index"></a>B. Creazione di un indice XML secondario  
 Nell'esempio seguente viene creato un indice XML secondario sulla colonna `CatalogDescription` della tabella `Production.ProductModel`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.indexes  
            WHERE name = N'IXML_ProductModel_CatalogDescription_Path')  
    DROP INDEX IXML_ProductModel_CatalogDescription_Path  
        ON Production.ProductModel;  
GO  
CREATE XML INDEX IXML_ProductModel_CatalogDescription_Path   
    ON Production.ProductModel (CatalogDescription)  
    USING XML INDEX PXML_ProductModel_CatalogDescription FOR PATH ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE SPATIAL INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [Indici XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Sys. xml_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Indici XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  

