---
title: table_constraint (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONSTRAINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table_constraint
ms.assetid: ac2a11e0-cc77-4e27-b107-4fe5bc6f5195
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 464ce13d973f975fe36a73f94ec9b12cd0eb1bf3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-table-tableconstraint-transact-sql"></a>ALTER TABLE table_constraint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Specifica le proprietà di una definizione DEFAULT aggiunta a una tabella tramite, un vincolo CHECK, FOREIGN KEY, UNIQUE o una chiave primaria [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ CONSTRAINT constraint_name ]   
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        (column [ ASC | DESC ] [ ,...n ] )  
        [ WITH FILLFACTOR = fillfactor   
        [ WITH ( <index_option>[ , ...n ] ) ]  
        [ ON { partition_scheme_name ( partition_column_name ... )  
          | filegroup | "default" } ]   
    | FOREIGN KEY   
        ( column [ ,...n ] )  
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | DEFAULT constant_expression FOR column [ WITH VALUES ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 CONSTRAINT  
 Specifica l'inizio di una definizione di un vincolo PRIMARY KEY, UNIQUE, FOREIGN KEY o CHECK oppure di una definizione DEFAULT.  
  
 *constraint_name*  
 Nome del vincolo. I nomi di vincolo devono seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md), ad eccezione del fatto che il nome non può iniziare con un simbolo di cancelletto (#). Se constraint_name viene omesso, al vincolo viene assegnato un nome generato dal sistema.  
  
 PRIMARY KEY  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. È possibile creare un solo vincolo PRIMARY KEY per ogni tabella.  
  
 UNIQUE  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco.  
  
 CLUSTERED | NONCLUSTERED  
 Imposta la creazione di un indice cluster o non cluster per il vincolo PRIMARY KEY o UNIQUE. Per impostazione predefinita per i vincoli PRIMARY KEY è impostata l'opzione CLUSTERED. Per impostazione predefinita per i vincoli UNIQUE è impostata l'opzione NONCLUSTERED.  
  
 Se in una tabella esiste già un vincolo o un indice cluster, non è possibile specificare l'opzione CLUSTERED. In questo caso, inoltre, i vincoli PRIMARY KEY sono impostati su NONCLUSTERED.  
  
 Colonne di **ntext**, **testo**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, o **immagine** tipi di dati non possono essere specificati come colonne di un indice.  
  
 *colonna*  
 Colonna o elenco di colonne tra parentesi utilizzate in un nuovo vincolo.  
  
 [ **ASC** | DESC]  
 Specifica l'ordinamento della colonna o delle colonne che fanno parte dei vincoli di tabella. Il valore predefinito è ASC.  
  
 CON valore FILLFACTOR  **=**  *fattore di riempimento*  
 Specifica la percentuale utilizzata da [!INCLUDE[ssDE](../../includes/ssde-md.md)] per riempire ogni pagina dell'indice utilizzata per archiviare dati dell'indice. Specificato dall'utente *fillfactor* valori possono essere compresi tra 1 e 100. Se non viene specificato alcun valore, il valore predefinito è 0.  
  
> [!IMPORTANT]  
>  Documentazione con FILLFACTOR = *fillfactor* come l'unica opzione di indice che si applica ai vincoli PRIMARY KEY o UNIQUE viene mantenuto per compatibilità con le versioni precedenti, ma non sarà più documentata in futuro in questo modo rilascia. È possono specificare altre opzioni di indice di [index_option](../../t-sql/statements/alter-table-index-option-transact-sql.md) clausola dell'istruzione ALTER TABLE.  
  
 ON { *partition_scheme_name***(***partition_column_name***)** | *filegroup* |  **"**predefinito**"** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il percorso di archiviazione dell'indice creato per il vincolo. Se *partition_scheme_name* è specificato, l'indice viene partizionato e le partizioni vengono eseguito il mapping ai filegroup specificati da *partition_scheme_name*. Se *filegroup* viene specificato, viene creato l'indice nel filegroup specificato. Se **"**predefinito**"** è specificato o se ON non è specificato, l'indice viene creato nello stesso filegroup della tabella. Se si specifica ON quando si aggiunge un indice cluster per un vincolo PRIMARY KEY o UNIQUE, l'intera tabella viene spostata nel filegroup specificato durante la creazione dell'indice cluster.  
  
 In questo contesto, default non è una parola chiave. è un identificatore per il filegroup predefinito e deve essere delimitato, ad esempio ON **"**predefinito**"** oppure ON **[**predefinito**]**. Se **"**predefinito**"** viene specificato, l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. Si tratta dell'impostazione predefinita.  
  
 FOREIGN KEY REFERENCES  
 Vincolo che impone l'integrità referenziale per i dati nella colonna. Per i vincoli FOREIGN KEY è necessario che ogni valore della colonna esista nella colonna specificata della tabella a cui viene fatto riferimento.  
  
 *referenced_table_name*  
 Tabella a cui fa riferimento il vincolo FOREIGN KEY.  
  
 *ref_column*  
 Colonna o elenco di colonne tra parentesi a cui fa riferimento il nuovo vincolo FOREIGN KEY.  
  
 ELIMINAZIONE { **ALCUNA AZIONE** | CASCADE | SET NULL | IMPOSTAZIONE DEL VALORE PREDEFINITO}  
 Specifica quale azione si verifica nelle righe della tabella che viene modificata se tali righe includono una relazione referenziale e se la riga a cui viene fatto riferimento viene eliminata dalla tabella padre. Il valore predefinito è NO ACTION.  
  
 NO ACTION  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] genera un errore e viene eseguito il rollback dell'azione di eliminazione della riga nella tabella padre.  
  
 CASCADE  
 Le righe corrispondenti vengono eliminate dalla tabella di riferimento se la riga viene eliminata dalla tabella padre.  
  
 SET NULL  
 Tutti i valori che costituiscono la chiave esterna vengono impostati su NULL quando viene eliminata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che le colonne chiave esterna ammettano valori Null.  
  
 SET DEFAULT  
 Tutti i valori che costituiscono la chiave esterna vengono impostati sui valori predefiniti quando viene eliminata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che per tutte le colonne chiave esterna siano definiti valori predefiniti. Se una colonna ammette valori Null e non viene impostato un valore predefinito esplicito, NULL diventa il valore predefinito implicito della colonna.  
  
 Non specificare CASCADE se la tabella verrà inclusa in una pubblicazione di tipo merge che utilizza record logici. Per altre informazioni sui record logici, vedere [Raggruppare modifiche alle righe correlate con record logici](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Non è possibile definire ON DELETE CASCADE se esiste già un trigger INSTEAD OF per ON DELETE nella tabella che viene modificata.  
  
 Ad esempio, nel [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, il **ProductVendor** tabella ha una relazione referenziale con la **fornitore** tabella. Il **ProductVendor** riferimenti di chiave esterna di **vendorID** chiave primaria.  
  
 Se viene eseguita un'istruzione DELETE in una riga il **fornitore** tabella e un'azione ON DELETE CASCADE viene specificata per **ProductVendor**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] verifica la presenza di uno o più righe dipendenti di **ProductVendor** tabella. Le eventuali righe dipendenti nella **ProductVendor** tabella verrà eliminata assieme alla riga a cui fa riferimento il **fornitore** tabella.  
  
 Al contrario, se si specifica NO ACTION, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore ed eseguire il rollback dell'azione di eliminazione **fornitore** riga quando esiste almeno una riga nel **ProductVendor** tabella cui fa riferimento.  
  
 AGGIORNAMENTO { **ALCUNA AZIONE** | CASCADE | SET NULL | IMPOSTAZIONE DEL VALORE PREDEFINITO}  
 Specifica l'azione eseguita nelle righe della tabella modificata se tali righe includono una relazione referenziale e la riga a cui viene fatto riferimento è stata aggiornata nella tabella padre. Il valore predefinito è NO ACTION.  
  
 NO ACTION  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore e viene eseguito il rollback dell'azione di aggiornamento della riga nella tabella padre.  
  
 CASCADE  
 Le righe corrispondenti vengono aggiornate nella tabella di riferimento quando la riga viene aggiornata nella tabella padre.  
  
 SET NULL  
 Tutti i valori che costituiscono la chiave esterna vengono impostati su NULL quando viene aggiornata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che le colonne chiave esterna ammettano valori Null.  
  
 SET DEFAULT  
 Tutti i valori che costituiscono la chiave esterna vengono impostati sui rispettivi valori predefiniti quando viene aggiornata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che per tutte le colonne chiave esterna siano definiti valori predefiniti. Se una colonna ammette valori Null e non viene impostato un valore predefinito esplicito, NULL diventa il valore predefinito implicito della colonna.  
  
 Non specificare CASCADE se la tabella verrà inclusa in una pubblicazione di tipo merge che utilizza record logici. Per altre informazioni sui record logici, vedere [Raggruppare modifiche alle righe correlate con record logici](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Non è possibile specificare ON UPDATE CASCADE, SET NULL o SET DEFAULT se nella tabella che viene modificata esiste già un trigger INSTEAD OF per ON UPDATE.  
  
 Ad esempio, nel [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, il **ProductVendor** tabella ha una relazione referenziale con la **fornitore** tabella. Il **ProductVendor** riferimenti di chiave esterna di **vendorID** chiave primaria.  
  
 Se viene eseguita un'istruzione UPDATE in una riga il **fornitore** tabella e un'azione ON UPDATE CASCADE viene specificata per **ProductVendor**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] verifica la presenza di uno o più righe dipendenti di **ProductVendor** tabella. Eventuale riga dipendente nella **ProductVendor** tabella verrà aggiornata, insieme alla riga a cui fa riferimento il **fornitore** tabella.  
  
 Al contrario, se si specifica NO ACTION, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore ed eseguire il rollback dell'azione di aggiornamento **fornitore** riga quando esiste almeno una riga nel **ProductVendor** tabella cui fa riferimento.  
  
 NOT FOR REPLICATION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Questa clausola può essere specificata per i vincoli FOREIGN KEY e CHECK. Se per un vincolo si specifica questa clausola, il vincolo non viene imposto quando gli agenti di replica eseguono le operazioni di inserimento, aggiornamento o eliminazione.  
  
 DEFAULT  
 Specifica il valore predefinito per la colonna. Le definizioni DEFAULT possono essere utilizzate per assegnare valori a una nuova colonna nelle righe di dati esistenti. Non è possibile aggiungere le definizioni DEFAULT alle colonne che contengono un **timestamp** tipo di dati, una proprietà IDENTITY, una definizione DEFAULT esistente o un valore predefinito associato. Se alla colonna è associato un valore predefinito, è necessario rimuoverlo prima di aggiungere il nuovo valore predefinito. Se è specificato un valore predefinito per una colonna di tipo definito dall'utente, il tipo deve supportare una conversione implicita da *constant_expression* per il tipo definito dall'utente. Per garantire la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile assegnare un nome di vincolo a una definizione DEFAULT.  
  
 *constant_expression*  
 Valore letterale, valore Null o funzione di sistema utilizzato come valore predefinito della colonna. Se *constant_expression* viene utilizzata in combinazione con una colonna definita per essere di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] tipo definito dall'utente, l'implementazione del tipo deve supportare una conversione implicita dal *constant_ espressione* per il tipo definito dall'utente.  
  
 PER *colonna*  
 Specifica la colonna associata a una definizione DEFAULT a livello di tabella.  
  
 WITH VALUES  
 Specifica che il valore predefinito fornito *constant_expression* viene archiviato in una nuova colonna che viene aggiunto alle righe esistenti. È possibile specificare la clausola WITH VALUES solo quando viene specificato DEFAULT in una clausola ADD di colonna. Se la colonna aggiunta ammette valori Null e viene specificata la clausola WITH VALUES, il valore predefinito viene archiviato nella nuova colonna aggiunta alle righe esistenti. Se per le colonne che ammettono valori Null la clausola WITH VALUES non viene specificata, il valore NULL viene archiviato nella nuova colonna nelle righe esistenti. Se la nuova colonna non ammette valori Null, il valore predefinito viene archiviato nelle nuove righe, indipendentemente dal fatto che la clausola WITH VALUES sia o meno specificata.  
  
 CHECK  
 Vincolo che impone l'integrità di dominio tramite la limitazione dei valori che è possibile inserire in una o più colonne.  
  
 *Logical_Expression*  
 Espressione logica utilizzata in un vincolo CHECK che restituisce TRUE o FALSE. *Logical_Expression* utilizzato con vincoli CHECK non può fare riferimento a un'altra tabella ma può fare riferimento altre colonne nella stessa tabella per la stessa riga. L'espressione non può fare riferimento a un tipo di dati alias.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si aggiungono vincoli FOREIGN KEY o CHECK, in tutti i dati esistenti viene verificata la presenza di eventuali violazioni dei vincoli, a meno che non venga specificata l'opzione WITH NOCHECK. Se si verificano violazioni, l'istruzione ALTER TABLE ha esito negativo e viene restituito un errore. Quando si aggiunge un nuovo vincolo PRIMARY KEY o UNIQUE a colonne esistenti, i dati delle colonne devono essere univoci. Se vengono individuati valori duplicati, l'istruzione ALTER TABLE ha esito negativo. L'opzione WITH NOCHECK non ha alcun effetto quando si aggiungono vincoli PRIMARY KEY o UNIQUE.  
  
 Ogni vincolo PRIMARY KEY e UNIQUE genera un indice. Il numero di vincoli UNIQUE e PRIMARY KEY non deve generare un numero di indici della tabella maggiore di 999 nel caso di indici non cluster e maggiore di 1 nel caso di indici cluster. I vincoli di chiave esterna non generano automaticamente un indice. Le colonne chiave esterna, tuttavia, vengono in genere utilizzate in criteri di join nelle query confrontando le colonne nel vincolo di chiave esterna di una tabella con le colonne chiave primaria o univoca nell'altra tabella. Un indice nelle colonne chiave esterna consente a [!INCLUDE[ssDE](../../includes/ssde-md.md)] di trovare rapidamente i dati correlati nella tabella della chiave esterna.  
  
## <a name="examples"></a>Esempi  
 Per esempi, vedere [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
