---
title: CREARE l'indice full-text (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXT_INDEX_TSQL
- CREATE_FULLTEXT_INDEX_TSQL
- CREATE FULLTEXT INDEX
- FULLTEXT INDEX
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], creating
- index creation [SQL Server], CREATE FULLTEXT INDEX statement
- CREATE FULLTEXT INDEX statement
ms.assetid: 8b80390f-5f8b-4e66-9bcc-cabd653c19fd
caps.latest.revision: 110
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 92749ed0518de83be07c6a80f9e3306741507166
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-fulltext-index-transact-sql"></a>CREATE FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un indice full-text per una tabella o una vista indicizzata di un database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È consentito un solo indice full-text per tabella o vista indicizzata e ogni indice full-text viene applicato a una singola tabella o vista indicizzata. Un indice full-text può contenere fino a 1024 colonne.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE FULLTEXT INDEX ON table_name  
   [ ( { column_name   
             [ TYPE COLUMN type_column_name ]  
             [ LANGUAGE language_term ]   
             [ STATISTICAL_SEMANTICS ]  
        } [ ,...n]   
      ) ]  
    KEY INDEX index_name   
    [ ON <catalog_filegroup_option> ]  
    [ WITH [ ( ] <with_option> [ ,...n] [ ) ] ]  
[;]  
  
<catalog_filegroup_option>::=  
 {  
    fulltext_catalog_name   
 | ( fulltext_catalog_name, FILEGROUP filegroup_name )  
 | ( FILEGROUP filegroup_name, fulltext_catalog_name )  
 | ( FILEGROUP filegroup_name )  
 }  
  
<with_option>::=  
 {  
   CHANGE_TRACKING [ = ] { MANUAL | AUTO | OFF [, NO POPULATION ] }   
 | STOPLIST [ = ] { OFF | SYSTEM | stoplist_name }  
 | SEARCH PROPERTY LIST [ = ] property_list_name   
 }  
```  
  
## <a name="arguments"></a>Argomenti  
 *table_name*  
 Nome della tabella o della vista indicizzata contenente la colonna o le colonne incluse nell'indice full-text.  
  
 *column_name*  
 Nome della colonna inclusa nell'indice full-text. Solo le colonne di tipo **char**, **varchar**, **nchar**, **nvarchar**, **testo**,  **ntext**, **immagine**, **xml**, e **varbinary (max)** può essere indicizzato per la ricerca full-text. Per specificare più colonne, ripetere il *column_name* clausola come indicato di seguito:  
  
 CREATE FULLTEXT INDEX ON *table_name* (*column_name1* […], *column_name2* […])...  
  
 COLONNA di tipo *type_column_name*  
 Specifica il nome di una colonna di tabella, *type_column_name*, che viene utilizzato per contenere il tipo di documento per un **varbinary (max)** o **immagine** documento. Questa colonna, nota come colonna di tipo, contiene un'estensione di file fornita dall'utente (doc, pdf, xls e così via). La colonna del tipo deve essere di tipo **char**, **nchar**, **varchar**o **nvarchar**.  
  
 Specificare TYPE COLUMN *type_column_name* solo se *column_name* specifica un **varbinary (max)** o **immagine** colonna, in cui si dati archiviati come dati binari; in caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore.  
  
> [!NOTE]  
>  In fase di indicizzazione, il motore Full-Text utilizza l'abbreviazione nella colonna di tipo di ogni riga della tabella per identificare il filtro di ricerca full-text da utilizzare per il documento in *column_name*. Il filtro carica il documento come flusso binario, rimuove le informazioni sulla formattazione e invia il testo dal documento al componente word breaker. Per altre informazioni, vedere [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md).  
  
 LINGUA *language_term*  
 È la lingua dei dati archiviati *column_name*.  
  
 *language_term* è facoltativo e può essere specificato come stringa, intero o esadecimale corrispondente all'identificatore delle impostazioni locali (LCID) di una lingua. Se non viene specificato alcun valore, viene utilizzata la lingua predefinita dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se *language_term* è specificato, la lingua rappresentata verrà utilizzato per indicizzare i dati archiviati in **char**, **nchar**, **varchar**, **nvarchar**, **testo**, e **ntext** colonne. Questo linguaggio è la lingua predefinita utilizzata in fase di query se *language_term* non è specificato come parte di un predicato full-text sulla colonna.  
  
 Quando specificato come stringa, *language_term* corrisponde al valore della colonna alias nella tabella di sistema syslanguages. La stringa deve essere racchiuso tra virgolette singole, come **'***language_term***'**. Quando specificato come un numero intero, *language_term* è l'identificatore LCID effettivo che identifica la lingua. Quando specificato come valore esadecimale, *language_term* è 0x seguito dal valore esadecimale del LCID. Il valore esadecimale deve essere composto al massimo da otto cifre, zero iniziali inclusi.  
  
 Se il valore è in formato DBCS (Double-Byte Character Set), verrà convertito in Unicode da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Risorse, quali word breaker e stemmer, devono essere abilitate per la lingua specificata come *language_term*. Se tali risorse non supportano la lingua specificata, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituirà un errore.  
  
 Utilizzare la stored procedure sp_configure per accedere alle informazioni sulla lingua full-text predefinita dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 Per le colonne di tipo non BLOB e non XML che contengono dati di testo in più lingue oppure nei casi in cui la lingua del testo archiviato nella colonna è sconosciuta, potrebbe essere appropriato utilizzare la risorsa per la lingua neutra (0x0). È tuttavia necessario considerare prima le possibili conseguenze derivanti dall'utilizzo di tale risorsa. Per informazioni sulle possibili soluzioni e conseguenze dell'uso della risorsa (0x0) lingua neutra, vedere [scegliere una lingua durante la creazione di un indice Full-Text](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  
  
 Per i documenti archiviati in colonne di tipo XML o BLOB, in fase di indicizzazione verrà utilizzata la codifica di lingua del documento. Ad esempio, nelle colonne XML, il **XML: lang** la lingua è identificata dall'attributo nei documenti XML. In fase di query, il valore specificato in precedenza *language_term* diventa la lingua predefinita utilizzata per le query full-text, a meno che non *language_term* è specificato come parte di una query full-text.  
  
 STATISTICAL_SEMANTICS  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Consente di creare la frase chiave aggiuntiva e gli indici di somiglianza dei documenti che fanno parte dell'indicizzazione semantica statistica. Per altre informazioni, vedere [Ricerca semantica &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).  
  
 INDICE di chiave *index_name*  
 È il nome dell'indice di chiave univoca in *table_name*. KEY INDEX deve essere una colonna chiave singola univoca che non ammette i valori Null. Selezionare l'indice di chiave univoca più piccolo possibile per la chiave univoca full-text.  Per prestazioni ottimali, si consiglia di utilizzare un tipo di dati integer per la chiave full-text.  
  
 *fulltext_catalog_name*  
 Catalogo full-text utilizzato per l'indice full-text. Il catalogo deve esistere nel database corrente. Questa clausola è facoltativa. Se non viene specificata, viene utilizzato un catalogo predefinito. Se non esiste alcun catalogo predefinito, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore.  
  
 FILEGROUP *filegroup_name*  
 Crea l'indice full-text specificato nel filegroup specificato. Il filegroup deve essere già esistente. Se la clausola FILEGROUP non viene specificata, l'indice full-text viene posizionato nello stesso filegroup della tabella o della vista di base nel caso di una tabella non partizionata o nel filegroup primario nel caso di una tabella partizionata.  
  
 CHANGE_TRACKING [=] {MANUALE | **AUTO** | DISATTIVAZIONE [, NO POPULATION]}  
 Specifica se le modifiche (aggiornamenti, eliminazioni o inserimenti) apportate alle colonne della tabella coperte dall'indice full-text verranno propagate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'indice full-text. Le modifiche apportate ai dati tramite WRITETEXT e UPDATETEXT non vengono riflesse nell'indice full-text, pertanto non vengono registrate dalla funzione di rilevamento delle modifiche.  
  
 MANUAL  
 Specifica che le modifiche rilevate devono essere propagate manualmente chiamando l'istruzione ALTER FULLTEXT INDEX... START UPDATE POPULATION [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione (*popolamento manuale*). Per chiamare questa istruzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodicamente, è possibile utilizzare [!INCLUDE[tsql](../../includes/tsql-md.md)] Agent.  
  
 **AUTOMATICO**  
 Specifica che le modifiche rilevate verranno propagate automaticamente modifica dei dati nella tabella di base (*il popolamento automatico*). Sebbene le modifiche vengano propagate automaticamente, tali modifiche potrebbero non risultare immediatamente nell'indice full-text. AUTO è l'impostazione predefinita.  
  
 OFF [ `,` NO POPULATION]  
 Specifica che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non mantiene un elenco delle modifiche apportate ai dati indicizzati. Se non si specifica NO POPULATION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] popola l'indice completamente dopo che è stato creato.  
  
 L'opzione NO POPULATION può essere utilizzata solo se l'impostazione di CHANGE_TRACKING è OFF. Se si specifica NO POPULATION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non popola un indice dopo che è stato creato. L'indice viene popolato solo dopo avere eseguito il comando ALTER FULLTEXT INDEX con la clausola START FULL POPULATION o START INCREMENTAL POPULATION.  
  
 ELENCO DI PAROLE NON SIGNIFICATIVE [=] {OFF | **Sistema** | *stoplist_name* }  
 Associa un elenco di parole non significative full-text all'indice. L'indice non viene popolato con alcun token che faccia parte dell'elenco di parole non significative specificato. Se non si specifica STOPLIST, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associa l'elenco di parole non significative full-text di sistema all'indice.  
  
 OFF  
 Specifica che all'indice full-text non deve essere associato alcun elenco di parole non significative.  
  
 **SISTEMA**  
 Specifica che per l'indice full-text deve essere utilizzato l'elemento STOPLIST full-text di sistema predefinito.  
  
 *stoplist_name*  
 Specifica il nome dell'elenco di parole non significative da associare all'indice full-text.  
  
 ELENCO delle proprietà di ricerca [=] *property_list_name*  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Associa un elenco di proprietà di ricerca all'indice.  
  
 OFF  
 Specifica che all'indice full-text non deve essere associato alcun elenco di proprietà.  
  
 *property_list_name*  
 Specifica il nome dell'elenco delle proprietà di ricerca da associare all'indice full-text.  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sugli indici full-text, vedere [creare e gestire indici Full-Text](../../relational-databases/search/create-and-manage-full-text-indexes.md).  
  
 In **xml** colonne, è possibile creare un indice full-text che indicizza il contenuto degli elementi XML, ma ignora il markup XML. Ai valori di attributo viene applicata l'indicizzazione full-text a meno che non siano valori numerici. I tag elemento sono utilizzati come limiti del token. Sono supportati documenti e frammenti XML o HTML ben formati e contenenti più lingue. Per altre informazioni, vedere [Utilizzo della ricerca full-text con colonne XML](../../relational-databases/xml/use-full-text-search-with-xml-columns.md).  
  
 Si consiglia di utilizzare un tipo di dati integer per la colonna chiave indice per consentire l'ottimizzazione durante l'esecuzione della query.  
  
## <a name="interactions-of-change-tracking-and-no-population-parameter"></a>Interazioni del rilevamento delle modifiche con NO POPULATION  
 Il popolamento dell'indice full-text dipende dal fatto che il rilevamento delle modifiche sia o meno abilitato e che si specifichi o meno WITH NO POPULATION nell'istruzione ALTER FULLTEXT INDEX. Nella tabella seguente è riepilogato il risultato di tale interazione.  
  
|Rilevamento modifiche|WITH NO POPULATION|Risultato|  
|---------------------|------------------------|------------|  
|Non abilitato|Non specificato|Viene eseguito un popolamento completo dell'indice.|  
|Non abilitato|Specified|L'indice non viene popolato fino a quando non viene eseguita un'istruzione ALTER FULLTEXT INDEX...START POPULATION.|  
|Abilitata|Specified|Viene generato un errore e l'indice non viene modificato.|  
|Abilitata|Non specificato|Viene eseguito un popolamento completo dell'indice.|  
  
 Per ulteriori informazioni sul popolamento di indici full-text, vedere [popolamento degli indici Full-Text](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre dell'autorizzazione REFERENCES nel catalogo full-text e dell'autorizzazione ALTER nella tabella o nella vista indicizzata oppure deve essere membro del ruolo predefinito del server sysadmin o del ruolo predefinito del database db_owner o db_ddladmin.  
  
 Se SET STOPLIST è specificato, l'utente deve disporre dell'autorizzazione REFERENCES nell'elenco di parole non significative specificato. Questa autorizzazione può essere concessa dal proprietario di STOPLIST.  
  
> [!NOTE]  
>  Agli utenti viene concessa l'autorizzazione REFERENCE per l'elenco di parole non significative predefinito fornito con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-unique-index-a-full-text-catalog-and-a-full-text-index"></a>A. Creazione di un indice univoco, un catalogo full-text e un indice full-text  
 Nell'esempio seguente viene creato un indice univoco sulla colonna `JobCandidateID` della tabella `HumanResources.JobCandidate` del database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Viene quindi creato un catalogo full-text predefinito, `ft` e infine viene creato un indice full-text sulla colonna `Resume` utilizzando il catalogo `ft` e l'elenco di parole non significative del sistema.  
  
```  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH STOPLIST = SYSTEM;  
GO  
```  
  
### <a name="b-creating-a-full-text-index-on-several-table-columns"></a>B. Creazione di un indice full-text su diverse colonne della tabella  
 Nell'esempio seguente viene creato un catalogo full-text, `production_catalog`, nel database di esempio `AdventureWorks`. Nell'esempio viene quindi creato un indice full-text che utilizza questo nuovo catalogo. L'indice full-text è sulle colonne `ReviewerName`, `EmailAddress` e `Comments` di `Production.ProductReview`. Per ogni colonna, nell'esempio viene specificato l'identificatore LCID dell'inglese, `1033`, che identifica la lingua dei dati nelle colonne. Questo indice full-text utilizza un indice della chiave univoca esistente, `PK_ProductReview_ProductReviewID`. Come consigliato, questa chiave di indice è in una colonna di valori interi, `ProductReviewID`.  
  
```  
CREATE FULLTEXT CATALOG production_catalog;  
GO  
CREATE FULLTEXT INDEX ON Production.ProductReview  
 (   
  ReviewerName  
     Language 1033,  
  EmailAddress  
     Language 1033,  
  Comments   
     Language 1033       
 )   
  KEY INDEX PK_ProductReview_ProductReviewID   
      ON production_catalog;   
GO  
```  
  
### <a name="c-creating-a-full-text-index-with-a-search-property-list-without-populating-it"></a>C. Creazione di un indice full-text con un elenco di proprietà di ricerca senza popolarlo  
 Nell'esempio seguente viene creato un indice full-text sulle colonne `Title`, `DocumentSummary` e `Document` della tabella `Production.Document`. Nell'esempio viene specificato l'identificatore LCID dell'inglese, `1033`, che identifica la lingua dei dati delle colonne. Questo indice full-text utilizza il catalogo full-text predefinito e un indice della chiave univoca esistente, `PK_Document_DocumentID`. Come consigliato, questa chiave di indice è in una colonna di valori interi, `DocumentID`.  
  
 Nell'esempio viene inoltre specificato l'elenco di parole non significative SYSTEM. Specifica inoltre un elenco di proprietà di ricerca, `DocumentPropertyList`; per un esempio che crea l'elenco di proprietà, vedere [CREATE SEARCH PROPERTY LIST &#40; Transact-SQL &#41; ](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
 Nell'esempio viene specificato che il rilevamento delle modifiche è disabilitato e non viene eseguito il popolamento. In un secondo momento, durante le ore di minore attività, nell'esempio viene utilizzata un'istruzione ALTER FULLTEXT INDEX per avviare il popolamento completo del nuovo indice e abilitare il rilevamento delle modifiche automatico.  
  
```  
CREATE FULLTEXT INDEX ON Production.Document  
  (   
  Title  
      Language 1033,   
  DocumentSummary  
      Language 1033,   
  Document   
      TYPE COLUMN FileExtension  
      Language 1033   
  )  
  KEY INDEX PK_Document_DocumentID  
          WITH STOPLIST = SYSTEM, SEARCH PROPERTY LIST = DocumentPropertyList, CHANGE_TRACKING OFF, NO POPULATION;  
   GO  
```  
  
 In un secondo momento, in un orario di minore attività, l'indice viene popolato:  
  
```  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e gestione di indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Sys. fulltext_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  

