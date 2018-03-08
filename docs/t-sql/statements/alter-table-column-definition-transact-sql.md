---
title: column_definition (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_definition
- column_definition_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column_definition
- ALTER TABLE statement
- column properties [SQL Server]
- column definitions [SQL Server]
ms.assetid: a1742649-ca29-4d9b-9975-661cdbf18f78
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d50bda05bd0487a60e9a909500be2ea3d65fed92
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-table-columndefinition-transact-sql"></a>ALTER TABLE column_definition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica le proprietà di una colonna che vengono aggiunti a una tabella utilizzando [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
column_name <data_type>  
[ FILESTREAM ]  
[ COLLATE collation_name ]   
[ NULL | NOT NULL ]  
[   
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression [ WITH VALUES ]   
    | IDENTITY [ ( seed , increment ) ] [ NOT FOR REPLICATION ]   
]  
[ ROWGUIDCOL ]   
[ SPARSE ]   
[ ENCRYPTED WITH  
  ( COLUMN_ENCRYPTION_KEY = key_name ,  
      ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
      ALGORITHM =  'AEAD_AES_256_CBC_HMAC_SHA_256'   
  ) ]  
[ MASKED WITH ( FUNCTION = ' mask_function ') ]  
[ <column_constraint> [ ...n ] ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *column_name*  
 Nome della colonna da modificare, aggiungere o eliminare. *column_name* può contenere da 1 a 128 caratteri. Per le nuove colonne create con un tipo di dati timestamp *column_name* può essere omesso. Se non *column_name* specificato per un **timestamp** colonna tipo di dati, il nome **timestamp** viene utilizzato.  
  
 [ *type_schema_name***.** ] *type_name*  
 Tipo di dati della colonna che viene aggiunta e dello schema a cui appartiene.  
  
 *TYPE_NAME* può essere:  
  
-   Oggetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il tipo di dati di sistema.  
  
-   Tipo di dati alias basato su un tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per poter essere utilizzati in una definizione di tabella, i tipi di dati alias devono venire creati tramite CREATE TYPE.  
  
-   Oggetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] tipo definito dall'utente e lo schema a cui appartiene. Per poter essere utilizzato in una definizione di tabella, un tipo definito dall'utente (UDT) di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] deve venire creato tramite CREATE TYPE.  
  
 Se *type_schema_name* non viene specificato, il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] riferimenti *type_name* nell'ordine seguente:  
  
-   Tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Schema predefinito dell'utente corrente nel database corrente.  
  
-   Schema **dbo** nel database corrente.  
  
*precisione*  
 Precisione del tipo di dati specificato. Per ulteriori informazioni sui valori di precisione validi, vedere [precisione, scala e lunghezza &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
*scala*  
 Scala per il tipo di dati specificato. Per ulteriori informazioni sui valori di scala validi, vedere [precisione, scala e lunghezza &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
**Max**  
 Si applica solo al **varchar**, **nvarchar**, e **varbinary** tipi di dati. Vengono utilizzati per l'archiviazione di 2^31 byte di dati di tipo carattere e binari e 2^30 byte di dati Unicode.  
  
**CONTENUTO**  
 Specifica che ogni istanza di **xml** del tipo di dati *column_name* può contenere più elementi di livello superiore. Si applica solo al contenuto di **xml** dati digitare e può essere specificato solo se *xml_schema_collection* viene anche specificato. Se viene omesso, per impostazione predefinita viene utilizzato CONTENT.  
  
DOCUMENT  
 Specifica che ogni istanza di **xml** del tipo di dati *column_name* può contenere un solo elemento di primo livello. DOCUMENTO si applica solo al **xml** dati digitare e può essere specificato solo se *xml_schema_collection* viene anche specificato.  
  
 *xml_schema_collection*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo al **xml** il tipo di dati per l'associazione con il tipo di una raccolta XML schema. Prima di digitare un **xml** colonna a uno schema, lo schema è necessario innanzitutto creare nel database utilizzando [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
FILESTREAM  
 Facoltativamente è possibile specificare l'attributo di archiviazione FILESTREAM per la colonna che dispone di un *type_name* di **varbinary (max)**.  
  
 Quando viene specificato FILESTREAM per una colonna, la tabella deve includere anche una colonna del **uniqueidentifier** tipo di dati che dispone dell'attributo ROWGUIDCOL. Questa colonna non deve consentire valori Null e deve avere un vincolo a colonna singola UNIQUE o PRIMARY KEY. Il valore GUID per la colonna deve essere fornito da un'applicazione all'inserimento dei dati o da un vincolo DEFAULT che utilizza la funzione NEWID ().  
  
 Non è possibile eliminare la colonna ROWGUIDCOL, né modificare i vincoli correlati quando per la tabella è stata definita una colonna FILESTREAM. La colonna ROWGUIDCOL può essere eliminata solo dopo l'eliminazione dell'ultima colonna FILESTREAM.  
  
 Quando l'attributo di archiviazione FILESTREAM viene specificato per una colonna, tutti i valori per quella colonna vengono archiviati in un contenitore di dati FILESTREAM nel file system.  
  
 Per un esempio che illustra come utilizzare una definizione di colonna, vedere [FILESTREAM &#40; SQL Server &#41; ](../../relational-databases/blob/filestream-sql-server.md).  
  
COLLATE *collation_name*  
 Specifica le regole di confronto per la colonna. Se viene omesso, alla colonna vengono assegnate le regole di confronto predefinite del database. È possibile usare nomi di regole di confronto di Windows o SQL. Per un elenco e altre informazioni, vedere [windows_collation_name &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) e [SQL nome regole di confronto del Server &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 La clausola COLLATE consente di specificare le regole di confronto solo delle colonne di **char**, **varchar**, **nchar**, e **nvarchar** tipi di dati .  
  
 Per ulteriori informazioni sulla clausola COLLATE, vedere [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 NULL | NOT NULL  
 Determina se i valori Null sono supportati nella colonna. L'opzione NULL non è esattamente un vincolo, ma può essere specificata allo stesso modo di NOT NULL.  
  
[Vincolo *constraint_name* ]  
 Specifica l'inizio di una definizione del valore DEFAULT. Per garantire la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile assegnare un nome di vincolo a una definizione DEFAULT. *constraint_name* deve seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md), ad eccezione del fatto che il nome non può iniziare con un simbolo di cancelletto (#). Se *constraint_name* viene omesso, viene assegnato un nome generato dal sistema per la definizione predefinita.  
  
DEFAULT  
 Parola chiave che specifica il valore predefinito della colonna. Le definizioni DEFAULT possono essere utilizzate per assegnare valori a una nuova colonna nelle righe di dati esistenti. Impossibile applicare le definizioni DEFAULT a **timestamp** colonne o colonne con una proprietà IDENTITY. Se viene specificato un valore predefinito per una colonna di tipo definito dall'utente, il tipo deve supportare una conversione implicita da *constant_expression* per il tipo definito dall'utente.  
  
*constant_expression*  
 Valore letterale, valore Null o funzione di sistema utilizzati come valore predefinito della colonna. Se usato in combinazione con una colonna definita per essere di un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] tipo definito dall'utente, l'implementazione del tipo deve supportare una conversione implicita dal *constant_expression* per il tipo definito dall'utente.  
  
WITH VALUES  
 Specifica che il valore predefinito fornito *constant_expression* viene archiviato in una nuova colonna aggiunta alle righe esistenti. Se la colonna aggiunta ammette valori Null e viene specificata la clausola WITH VALUES, il valore predefinito viene archiviato nella nuova colonna aggiunta alle righe esistenti. Se per le colonne che ammettono valori Null la clausola WITH VALUES non viene specificata, il valore NULL viene archiviato nella nuova colonna nelle righe esistenti. Se la nuova colonna non ammette valori Null, il valore predefinito viene archiviato nelle nuove righe, indipendentemente dal fatto che la clausola WITH VALUES sia o meno specificata.  
  
IDENTITY  
 Specifica che la nuova colonna è una colonna Identity. Il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] fornisce un valore univoco incrementale per la colonna. Quando si aggiungono colonne identificatore alle tabelle esistenti, alle righe esistenti della tabella vengono aggiunti i valori Identity con i valori di inizializzazione e di incremento. L'ordine con cui le righe vengono aggiornate non è prevedibile. Vengono inoltre generati valori Identity per qualsiasi nuova riga aggiunta.  
  
 Le colonne Identity vengono comunemente utilizzate in combinazione con vincoli PRIMARY KEY per fungere da identificatore di riga univoco per la tabella. La proprietà IDENTITY può essere assegnata a un **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, o **numeric(p,0)** colonna. Ogni tabella può includere una sola colonna Identity. Per una colonna Identity inoltre non è possibile utilizzare la parola chiave DEFAULT con associati valori predefiniti. È necessario specificare sia il valore di inizializzazione che l'incremento oppure nessuno dei due valori. Nel secondo caso il valore predefinito è (1,1).  
  
> [!NOTE]  
>  Non è possibile modificare una colonna della tabella esistente per aggiungere la proprietà IDENTITY.  
  
 Non è possibile aggiungere una colonna Identity a una tabella pubblicata perché questo può impedire la convergenza quando le colonne vengono replicate nel Sottoscrittore. I valori della colonna Identity nel server di pubblicazione dipendono dall'ordine in cui vengono fisicamente archiviate le righe della tabella interessata. Le righe possono essere archiviate in modo diverso nel Sottoscrittore, pertanto il valore della colonna Identity può essere diverso per le stesse righe.  
  
 Per disabilitare la proprietà IDENTITY di una colonna per consentire i valori da inserire in modo esplicito, utilizzare [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md).  
  
*valore di inizializzazione*  
 Valore utilizzato per la prima riga caricata nella tabella.  
  
*incremento*  
 Valore incrementale aggiunto al valore Identity della riga precedente caricata.  
  
NOT FOR REPLICATION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Può essere specificato per la proprietà IDENTITY. Se si specifica questa clausola per la proprietà IDENTITY, i valori non vengono incrementati nelle colonne Identity quando gli agenti di replica eseguono operazioni di inserimento.  
  
ROWGUIDCOL  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che la colonna è una colonna GUID di riga. ROWGUIDCOL può essere assegnato solo a un **uniqueidentifier** e solo una colonna **uniqueidentifier** colonna per ogni tabella può essere definita come colonna ROWGUIDCOL. Non è possibile assegnare ROWGUIDCOL a colonne di tipo definito dall'utente (UDT).  
  
 La proprietà ROWGUIDCOL non impone l'univocità dei valori archiviati nella colonna. Inoltre non genera automaticamente valori per le nuove righe inserite nella tabella. Per generare valori univoci per ogni colonna, è necessario utilizzare la funzione NEWID con istruzioni INSERT o specificare la funzione NEWID come valore predefinito della colonna. Per ulteriori informazioni, vedere [NEWID &#40; Transact-SQL &#41; ](../../t-sql/functions/newid-transact-sql.md)e [INSERT &#40; Transact-SQL &#41; ](../../t-sql/statements/insert-transact-sql.md).  
  
SPARSE  
 Indica che la colonna è di tipo sparse. L'archiviazione delle colonne di tipo sparse è ottimizzata per valori Null. Non è possibile designare le colonne di tipo sparse come NOT NULL. Per ulteriori restrizioni e ulteriori informazioni sulle colonne di tipo sparse, vedere [utilizzare le colonne di tipo Sparse](../../relational-databases/tables/use-sparse-columns.md).  
  
\<column_constraint >  
 Per le definizioni degli argomenti di vincolo di colonna, vedere [column_constraint &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-column-constraint-transact-sql.md).  
  
 CRITTOGRAFATO CON  
 Specifica le colonne di crittografia utilizzando il [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) funzionalità.  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 Specifica la chiave di crittografia di colonna. Per ulteriori informazioni, vedere [CREATE COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
ENCRYPTION_TYPE = {DETERMINISTICA | CASUALE}  
 La**crittografia deterministica** usa un metodo che genera sempre lo stesso valore crittografato per qualsiasi valore di testo normale specificato. Uso della crittografia deterministica consente la ricerca utilizzando il confronto di uguaglianza, raggruppamento e join di tabelle con join di uguaglianza in base ai valori crittografati, ma può anche consentire agli utenti non autorizzati di indovinare le informazioni sui valori crittografati esaminando i criteri in la colonna crittografata. Unione di due tabelle sulle colonne crittografate in modo deterministico è possibile solo se entrambe le colonne vengono crittografate tramite la stessa chiave di crittografia di colonna. La crittografia deterministica deve usare regole di confronto a livello di colonna con un ordinamento binario2 per colonne di tipo carattere.  
  
 La**crittografia casuale** usa un metodo di crittografia dei dati meno prevedibile. La crittografia casuale è più sicura ma impedisce le ricerche di uguaglianza, raggruppamento e join su colonne crittografate. Le colonne con la crittografia casuale non possono essere indicizzate.  
  
 Per le colonne che saranno i parametri di ricerca o raggruppamento, ad esempio un numero di ID per enti pubblici, utilizzare la crittografia deterministica. Usare la crittografia casuale, per i dati, ad esempio un numero di carta di credito, che non è raggruppati con altri record o usati per il join di tabelle e che non viene cercato per perché utilizzare altre colonne (ad esempio un numero di transazioni) per trovare la riga che contiene crittografata colonna di interesse.  
  
 Le colonne devono essere di un tipo di dati validi.  
  
ALGORITMO  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
Deve essere **'AEAD_AES_256_CBC_HMAC_SHA_256'**.  
  
 Per ulteriori informazioni, inclusi i vincoli di funzionalità, vedere [Always Encrypted &#40; motore di Database &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
   
Aggiungere MASCHERATI con (funzione = ' *mask_function* ')  
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Specifica una maschera dati dinamica. *mask_function* è il nome della funzione di maschera con i parametri appropriati. Le funzioni seguenti sono disponibili:  
  
-   default)  
  
-   email()  
  
-   partial()  
  
-   funzione DISTRIB  
  
 Per i parametri di funzione, vedere [maschera dati dinamica](../../relational-databases/security/dynamic-data-masking.md).  
  
## <a name="remarks"></a>Osservazioni  
 Se viene aggiunta una colonna con un **uniqueidentifier** del tipo di dati, può essere definito con un valore predefinito che utilizza la funzione NEWID () per fornire i valori dell'identificatore univoco nella nuova colonna per ogni riga nella tabella.  
  
 In [!INCLUDE[ssDE](../../includes/ssde-md.md)] non è previsto un ordine specifico per DEFAULT, IDENTITY, ROWGUIDCOL o vincoli di colonna in una definizione di colonna.  
  
 L'istruzione ALTER TABLE avrà esito negativo se, a seguito dell'aggiunta della colonna, la dimensione della riga di dati supererà 8060 byte.  
  
## <a name="examples"></a>Esempi  
 Per esempi, vedere [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
