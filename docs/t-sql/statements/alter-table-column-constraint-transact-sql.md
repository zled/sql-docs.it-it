---
title: column_constraint (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_constraint
- column_constraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER TABLE statement
- constraints [SQL Server], properties
- constraints [SQL Server], definitions
- column_constraint
ms.assetid: 8119b7c7-e93b-4de5-8f71-c3b7c70b993c
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4f8238266e82aadeee973772266de1c74712f28
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-columnconstraint-transact-sql"></a>Column_constraint ALTER TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Specifica le proprietà di un vincolo PRIMARY KEY, FOREIGN KEY, UNIQUE o CHECK che fa parte di una nuova definizione di colonna aggiunta a una tabella tramite [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ CONSTRAINT constraint_name ]   
{   
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [ WITH FILLFACTOR = fillfactor ]   
        [ WITH ( index_option [, ...n ] ) ]  
        [ ON { partition_scheme_name (partition_column_name)   
            | filegroup | "default" } ]   
    | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name   
            [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 CONSTRAINT  
 Specifica l'inizio della definizione di un vincolo PRIMARY KEY, UNIQUE, FOREIGN KEY o CHECK.  
  
 *constraint_name*  
 Nome del vincolo. I nomi di vincolo devono seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md), ad eccezione del fatto che il nome non può iniziare con un simbolo di cancelletto (#). Se *constraint_name* viene omesso, il vincolo viene assegnato un nome generato dal sistema.  
  
 NULL | NOT NULL  
 Specifica se la colonna consente valori Null. È possibile aggiungere le colonne che non ammettono valori Null solo se a esse è associato un valore predefinito. Le nuove colonne che ammettono valori Null, ma a cui non è associato alcun valore predefinito contengono NULL per ogni riga della tabella. Se insieme a una nuova colonna che ammette valori Null viene aggiunta una definizione DEFAULT, è possibile specificare l'opzione WITH VALUES per la memorizzazione del valore predefinito nella nuova colonna per ogni riga della tabella.  
  
 Se la nuova colonna non consente valori Null, è necessario aggiungere una definizione DEFAULT assieme alla nuova colonna. La nuova colonna viene caricata automaticamente con il valore predefinito in ogni riga esistente delle nuove colonne.  
  
 Quando l'aggiunta di una colonna richiede la modifica fisica delle righe di dati di una tabella, ad esempio l'aggiunta di valori DEFAULT a ogni riga, durante l'esecuzione dell'istruzione ALTER TABLE vengono mantenuti attivi i blocchi sulla tabella. Ciò ha ripercussioni sulla possibilità di modificare il contenuto della tabella mentre i blocchi sono attivi. L'aggiunta di una colonna che ammette valori Null ma che non specifica un valore predefinito è solo un'operazione a livello di metadati che non richiede alcun blocco.  
  
 In caso di utilizzo dell'istruzione CREATE TABLE o ALTER TABLE, le impostazioni del database e della sessione influenzano e talvolta sostituiscono il supporto di valori Null del tipo di dati utilizzato in una definizione di colonna. È consigliabile definire sempre in modo esplicito una colonna come NULL o NOT NULL per le colonne non calcolate oppure, se si utilizza un tipo di dati definito dall'utente, consentire nella colonna l'utilizzo dell'impostazione predefinita relativa al supporto di valori Null per tale tipo di dati. Per altre informazioni, vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
 PRIMARY KEY  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. È possibile creare un solo vincolo PRIMARY KEY per ogni tabella.  
  
 UNIQUE  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco.  
  
 CLUSTERED | NONCLUSTERED  
 Imposta la creazione di un indice cluster o non cluster per il vincolo PRIMARY KEY o UNIQUE. Per impostazione predefinita per i vincoli PRIMARY KEY è impostata l'opzione CLUSTERED. Per impostazione predefinita per i vincoli UNIQUE è impostata l'opzione NONCLUSTERED.  
  
 Se in una tabella esiste già un vincolo o un indice cluster, non è possibile specificare l'opzione CLUSTERED. In questo caso, inoltre, i vincoli PRIMARY KEY sono impostati su NONCLUSTERED.  
  
 Colonne di **ntext**, **testo**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, o **immagine** tipi di dati non possono essere specificati come colonne di un indice.  
  
 CON valore FILLFACTOR  **=**  *fattore di riempimento*  
 Specifica la percentuale utilizzata da [!INCLUDE[ssDE](../../includes/ssde-md.md)] per riempire ogni pagina dell'indice utilizzata per archiviare dati dell'indice. I valori relativi al fattore di riempimento specificato dall'utente possono essere compreso tra 1 e 100. Se non viene specificato alcun valore, il valore predefinito è 0.  
  
> [!IMPORTANT]  
>  Documentazione con FILLFACTOR = *fillfactor* come l'unica opzione di indice che si applica ai vincoli PRIMARY KEY o UNIQUE viene mantenuto per compatibilità con le versioni precedenti, ma non sarà più documentata in futuro in questo modo rilascia. È possono specificare altre opzioni di indice di [index_option](../../t-sql/statements/alter-table-index-option-transact-sql.md) clausola dell'istruzione ALTER TABLE.  
  
 ON { *partition_scheme_name***(***partition_column_name***)** | *filegroup*  |  **"**predefinito**"** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il percorso di archiviazione dell'indice creato per il vincolo. Se *partition_scheme_name* è specificato, l'indice viene partizionato e le partizioni vengono eseguito il mapping ai filegroup specificati da *partition_scheme_name*. Se *filegroup* viene specificato, viene creato l'indice nel filegroup specificato. Se **"**predefinito**"** è specificato o se ON non è specificato, l'indice viene creato nello stesso filegroup della tabella. Se si specifica ON quando si aggiunge un indice cluster per un vincolo PRIMARY KEY o UNIQUE, l'intera tabella viene spostata nel filegroup specificato durante la creazione dell'indice cluster.  
  
 In questo contesto, default non è una parola chiave. È un identificatore per il filegroup predefinito e deve essere delimitato, ad esempio ON **"**predefinito**"** oppure ON **[**predefinito**]**. Se **"**predefinito**"** viene specificato, l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. Si tratta dell'impostazione predefinita. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 FOREIGN KEY REFERENCES  
 Vincolo che impone l'integrità referenziale per i dati nella colonna. Per i vincoli FOREIGN KEY è necessario che ogni valore della colonna esista nella colonna specificata della tabella a cui viene fatto riferimento.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella a cui il vincolo FOREIGN KEY fa riferimento.  
  
 *referenced_table_name*  
 Tabella a cui fa riferimento il vincolo FOREIGN KEY.  
  
 *ref_column*  
 Colonna tra parentesi a cui il nuovo vincolo FOREIGN KEY fa riferimento.  
  
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
  
 Non è possibile specificare ON DELETE CASCADE se nella tabella in fase di modifica esiste già un trigger INSTEAD OF ON DELETE.  
  
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
  
 Se viene eseguita un'istruzione UPDATE in una riga il **fornitore** tabella e un'azione ON UPDATE CASCADE viene specificata per **ProductVendor**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] verifica la presenza di uno o più righe dipendenti di **ProductVendor** tabella. Eventuale riga dipendente nella **ProductVendor** tabella verrà aggiornata assieme alla riga a cui fa riferimento il **fornitore** tabella.  
  
 Al contrario, se si specifica NO ACTION, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore ed eseguire il rollback dell'azione di aggiornamento **fornitore** riga quando esiste almeno una riga nel **ProductVendor** tabella cui fa riferimento.  
  
 NOT FOR REPLICATION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Questa clausola può essere specificata per i vincoli FOREIGN KEY e CHECK. Se per un vincolo si specifica questa clausola, il vincolo non viene imposto quando gli agenti di replica eseguono le operazioni di inserimento, aggiornamento o eliminazione.  
  
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
 [column_definition &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-column-definition-transact-sql.md)  
  
  

