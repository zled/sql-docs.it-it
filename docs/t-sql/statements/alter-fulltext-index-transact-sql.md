---
title: ALTER FULLTEXT INDEX (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER FULLTEXT INDEX
- ALTER_FULLTEXT_INDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- modifying full-text indexes
- full-text indexes [SQL Server], modifying
- search property lists [SQL Server], associating with full-text indexes
- ALTER FULLTEXT INDEX statement
ms.assetid: b6fbe9e6-3033-4d1b-b6bf-1437baeefec3
caps.latest.revision: 95
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 48861e0c85263e98333ea3fad6a4da0fa0674b1f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-fulltext-index-transact-sql"></a>ALTER FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifica le proprietà di un indice full-text in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER FULLTEXT INDEX ON table_name  
   { ENABLE   
   | DISABLE  
   | SET CHANGE_TRACKING [ = ] { MANUAL | AUTO | OFF }  
   | ADD ( column_name   
           [ TYPE COLUMN type_column_name ]   
           [ LANGUAGE language_term ]  
           [ STATISTICAL_SEMANTICS ]  
           [,...n]   
         )  
     [ WITH NO POPULATION ]  
   | ALTER COLUMN column_name  
     { ADD | DROP } STATISTICAL_SEMANTICS  
     [ WITH NO POPULATION ]  
   | DROP ( column_name [,...n] )  
     [ WITH NO POPULATION ]   
   | START { FULL | INCREMENTAL | UPDATE } POPULATION  
   | {STOP | PAUSE | RESUME } POPULATION   
   | SET STOPLIST [ = ] { OFF| SYSTEM | stoplist_name }  
     [ WITH NO POPULATION ]   
   | SET SEARCH PROPERTY LIST [ = ] { OFF | property_list_name }  
     [ WITH NO POPULATION ]   
   }  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *table_name*  
 Nome della tabella o della vista indicizzata contenente la colonna o le colonne incluse nell'indice full-text. I nomi dei proprietari del database e della tabella sono facoltativi.  
  
 ENABLE | DISABLE  
 Indica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se full-text di raccogliere dati dell'indice per *table_name*. ENABLE consente di attivare l'indice full-text, DISABLE di disabilitarlo. La tabella non supporterà query full-text mentre l'indice è disabilitato.  
  
 Disabilitare un indice full-text consente di disattivare il rilevamento delle modifiche conservando l'indice full-text, che può essere riattivato utilizzando ENABLE in qualsiasi momento. Quando l'indice full-text è disabilitato, i relativi metadati vengono mantenuti nelle tabelle di sistema. Se l'opzione CHANGE_TRACKING è abilitata (aggiornamento manuale o automatico) quando l'indice full-text è disabilitato, lo stato dell'indice viene bloccato, eventuali ricerche per indicizzazione in corso vengono arrestate e le nuove modifiche apportate ai dati della tabella non vengono registrate o propagate nell'indice.  
  
 SET CHANGE_TRACKING {MANUAL | AUTO | OFF}  
 Specifica se le modifiche (aggiornamenti, eliminazioni o inserimenti) apportate alle colonne della tabella coperte dall'indice full-text verranno propagate dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'indice full-text. Le modifiche apportate ai dati tramite WRITETEXT e UPDATETEXT non vengono riportate nell'indice full-text e pertanto non vengono registrate dalla funzione di rilevamento delle modifiche.  
  
> [!NOTE]  
>  Per informazioni sull'interazione del rilevamento delle modifiche e del parametro WITH NO POPULATION, vedere la sezione "Osservazioni" più avanti in questo argomento.  
  
 MANUAL  
 Specifica che le modifiche rilevate verranno propagate manualmente chiamando l'istruzione ALTER FULLTEXT INDEX … START UPDATE POPULATION [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione (*popolamento manuale*). Per chiamare questa istruzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodicamente, è possibile utilizzare [!INCLUDE[tsql](../../includes/tsql-md.md)] Agent.  
  
 AUTO  
 Specifica che le modifiche rilevate verranno propagate automaticamente modifica dei dati nella tabella di base (*il popolamento automatico*). Sebbene le modifiche vengano propagate automaticamente, tali modifiche potrebbero non risultare immediatamente nell'indice full-text. AUTO è l'impostazione predefinita.  
  
 OFF  
 Specifica che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non manterrà un elenco delle modifiche apportate ai dati indicizzati.  
  
 AGGIUNGERE | ELIMINARE *column_name*  
 Specifica le colonne da aggiungere o eliminare in un indice full-text. Le colonne devono essere di tipo **char**, **varchar**, **nchar**, **nvarchar**, **testo**, **ntext**, **immagine**, **xml**, **varbinary**, o **varbinary (max)**.  
  
 Utilizzare la clausola DROP solo per colonne abilitate in precedenza per l'indicizzazione full-text.  
  
 Utilizzare TYPE COLUMN e LANGUAGE con la clausola ADD per impostare queste proprietà di *column_name*. Se si aggiunge una colonna, è necessario ripopolare l'indice full-text della tabella per consentire il corretto funzionamento delle query full-text su tale colonna.  
  
> [!NOTE]  
>  Il popolamento dell'indice full-text dopo l'aggiunta o l'eliminazione di una colonna varia a seconda che sia abilitato il rilevamento delle modifiche e sia specificato WITH NO POPULATION. Per ulteriori informazioni, vedere la sezione "Note" più avanti in questo argomento.  
  
 COLONNA di tipo *type_column_name*  
 Specifica il nome di una colonna di tabella, *type_column_name*, che viene utilizzato per contenere il tipo di documento per un **varbinary**, **varbinary (max)**, o **immagine** documento. Questa colonna, nota come colonna di tipo, contiene un'estensione di file fornita dall'utente (doc, pdf, xls e così via). La colonna del tipo deve essere di tipo **char**, **nchar**, **varchar**o **nvarchar**.  
  
 Specificare TYPE COLUMN *type_column_name* solo se *column_name* specifica un **varbinary**, **varbinary (max)** o  **immagine** colonna, in cui dati vengono archiviati come dati binari; in caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore.  
  
> [!NOTE]  
>  In fase di indicizzazione, il motore Full-Text utilizza l'abbreviazione nella colonna di tipo di ogni riga della tabella per identificare il filtro di ricerca full-text da utilizzare per il documento in *column_name*. Il filtro carica il documento come flusso binario, rimuove le informazioni sulla formattazione e invia il testo dal documento al componente word breaker. Per altre informazioni, vedere [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md).  
  
 LINGUA *language_term*  
 È la lingua dei dati archiviati **column_name**.  
  
 *language_term* è facoltativo e può essere specificato come stringa, intero o esadecimale corrispondente all'identificatore delle impostazioni locali (LCID) di una lingua. Se *language_term* è specificato, la lingua rappresentata verrà applicata a tutti gli elementi della condizione di ricerca. Se viene specificato alcun valore, la lingua full-text predefinita del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene utilizzata l'istanza.  
  
 Utilizzare il **sp_configure** stored procedure per accedere alle informazioni sulla lingua predefinita full-text del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
 Quando specificato come stringa, *language_term* corrisponde al **alias** valore colonna il **syslanguages** tabella di sistema. La stringa deve essere racchiuso tra virgolette singole, come '*language_term*'. Quando specificato come un numero intero, *language_term* è l'identificatore LCID effettivo che identifica la lingua. Quando specificato come valore esadecimale, *language_term* è 0x seguito dal valore esadecimale del LCID. Il valore esadecimale deve essere composto al massimo da otto cifre, zero iniziali inclusi.  
  
 Se il valore è in formato DBCS (Double-Byte Character Set), verrà convertito in Unicode da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Risorse, quali word breaker e stemmer, devono essere abilitate per la lingua specificata come *language_term*. Se tali risorse non supportano la lingua specificata, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituirà un errore.  
  
 Utilizzare la risorsa per la lingua neutra (0x0) per le colonne non BLOB e non XML che contengono dati di testo in più lingue oppure nei casi in cui la lingua del testo archiviato nella colonna è sconosciuta. Per i documenti archiviati in colonne di tipo XML o BLOB, in fase di indicizzazione verrà utilizzata la codifica di lingua del documento. Nelle colonne XML, ad esempio, la lingua è identificata dall'attributo xml:lang nei documenti XML. In fase di query, il valore specificato in precedenza *language_term* diventa la lingua predefinita utilizzata per le query full-text, a meno che non *language_term* è specificato come parte di una query full-text.  
  
 STATISTICAL_SEMANTICS  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Consente di creare la frase chiave aggiuntiva e gli indici di somiglianza dei documenti che fanno parte dell'indicizzazione semantica statistica. Per altre informazioni, vedere [Ricerca semantica &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).  
  
 [ **,***... n*]  
 Indica che è possibile specificare più colonne per la clausola ADD, ALTER o DROP. Se si specificano più colonne, utilizzare la virgola come separatore.  
  
 WITH NO POPULATION  
 Specifica che l'indice full-text non verrà popolato dopo un'operazione ADD o DROP per le colonne o un'operazione SET STOPLIST. L'indice verrà popolato solo se si esegue un comando START...POPULATION.  
  
 Se si specifica NO POPULATION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non popola un indice. L'indice viene popolato solo quando si esegue un comando ALTER FULLTEXT INDEX...START POPULATION. Se non si specifica NO POPULATION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] popola l'indice.  
  
 Se l'opzione CHANGE_TRACKING è abilitata e si specifica WITH NO POPULATION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore. Se l'opzione CHANGE_TRACKING è abilitata e non viene specificato WITH NO POPULATION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue un popolamento completo dell'indice.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'interazione del rilevamento delle modifiche con WITH NO POPULATION, vedere la sezione "Osservazioni" più avanti in questo argomento.  
  
 {ADD | DROP } STATISTICAL_SEMANTICS  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Consente di abilitare o disabilitare l'indicizzazione semantica statistica per le colonne specificate. Per altre informazioni, vedere [Ricerca semantica &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).  
  
 START {FULL|INCREMENTAL|UPDATE} POPULATION  
 Indica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di avviare il popolamento dell'indice full-text di *table_name*. Se un popolamento dell'indice full-text è già in corso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un avviso e non viene avviato un nuovo popolamento.  
  
 FULL  
 Specifica che devono essere recuperate tutte le righe della tabella per l'indicizzazione full-text, anche se le righe sono già state indicizzate.  
  
 INCREMENTAL  
 Specifica che per l'indicizzazione full-text devono essere recuperate solo le righe modificate dopo l'ultimo popolamento. INCREMENTAL può essere applicato solo se la tabella ha una colonna di tipo **timestamp**. Se una tabella nel catalogo full-text non contiene una colonna di tipo **timestamp**, la tabella viene eseguito un popolamento completo.  
  
 UPDATE  
 Specifica che devono essere elaborate tutte le operazioni di inserimento, aggiornamento o eliminazione eseguite dopo l'ultimo aggiornamento dell'indice con rilevamento delle modifiche. È necessario che il popolamento con rilevamento delle modifiche sia abilitato per una tabella, ma l'indice ad aggiornamento in background o il rilevamento automatico delle modifiche non deve essere attivato.  
  
 {STOP | PAUSE | RESUME } POPULATION  
 Arresta o sospende qualsiasi popolamento in corso oppure arresta o riprende qualsiasi popolamento sospeso.  
  
 STOP POPULATION non arresta il rilevamento automatico delle modifiche o l'indice ad aggiornamento in background. Per arrestare il rilevamento delle modifiche, utilizzare SET CHANGE_TRACKING OFF.  
  
 PAUSE POPULATION e RESUME POPULATION possono essere utilizzati soltanto per popolamenti completi. Non sono rilevanti per altri tipi di popolamento poiché le ricerche per indicizzazione vengono riprese negli altri popolamenti dal punto in cui sono state arrestate.  
  
 ELENCO DI PAROLE NON SIGNIFICATIVE SET {OFF | SISTEMA | *stoplist_name* }  
 Cambia l'elenco di parole non significative full-text associato all'indice, se presente.  
  
 OFF  
 Specifica che all'indice full-text non deve essere associato alcun elenco di parole non significative.  
  
 SYSTEM  
 Specifica che per l'indice full-text deve essere utilizzato l'elemento STOPLIST full-text di sistema predefinito.  
  
 *stoplist_name*  
 Specifica il nome dell'elenco di parole non significative da associare all'indice full-text.  
  
 Per altre informazioni, vedere [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
 SET SEARCH PROPERTY LIST {OFF | *property_list_name* } [WITH NO POPULATION]  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Modifica l'elenco delle proprietà di ricerca associate all'indice, se presente.  
  
 OFF  
 Specifica che all'indice full-text non deve essere associato alcun elenco di proprietà. Quando si disattiva l'elenco delle proprietà di ricerca di un indice full-text (ALTER FULLTEXT INDEX … SET SEARCH PROPERTY LIST OFF), non sarà più possibile eseguire la ricerca delle proprietà nella tabella di base.  
  
 Per impostazione predefinita, quando si disattiva un elenco delle proprietà di ricerca esistente, l'indice full-text viene ripopolato automaticamente. Se si specifica WITH NO POPULATION quando si disattiva l'elenco delle proprietà di ricerca, il ripopolamento automatico non ha luogo. È tuttavia consigliabile eseguire un popolamento completo su questo indice full-text. Il ripopolamento dell'indice full-text comporta la rimozione dei metadati specifici di ogni proprietà di ricerca eliminata, rendendo più piccolo e più efficiente l'indice full-text.  
  
 *property_list_name*  
 Specifica il nome dell'elenco delle proprietà di ricerca da associare all'indice full-text.  
  
 L'aggiunta di un elenco delle proprietà di ricerca a un indice full-text richiede il ripopolamento dell'indice per indicizzare le proprietà di ricerca registrate per l'elenco delle proprietà di ricerca associato. Se si specifica WITH NO POPULATION quando si aggiunge l'elenco delle proprietà di ricerca, è necessario eseguire un popolamento sull'indice, in un momento appropriato.  
  
> [!IMPORTANT]  
>  Se l'indice full-text è stato in precedenza associato a una ricerca diversa, è necessario ricostruire l'elenco delle proprietà per rendere coerente lo stato dell'indice. L'indice viene troncato immediatamente e rimane vuoto fino al termine del popolamento completo. Per ulteriori informazioni sulle situazioni in cui la modifica dell'elenco delle proprietà di ricerca richiede la ricompilazione, vedere le osservazioni più avanti in questo argomento.  
  
> [!NOTE]  
>  È possibile associare un elenco delle proprietà di ricerca specificato a più indici full-text nello stesso database.  
  
 **Per trovare la proprietà di ricerca sono elencati nel database corrente**  
  
-   [registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 Per ulteriori informazioni sugli elenchi di proprietà di ricerca, vedere [ricerca proprietà dei documenti con elenchi di proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="interactions-of-change-tracking-and-no-population-parameter"></a>Interazioni del rilevamento delle modifiche con NO POPULATION  
 Il popolamento dell'indice full-text dipende dal fatto che il rilevamento delle modifiche sia o meno abilitato e che si specifichi o meno WITH NO POPULATION nell'istruzione ALTER FULLTEXT INDEX. Nella tabella seguente è riepilogato il risultato di tale interazione.  
  
|Rilevamento modifiche|WITH NO POPULATION|Risultato|  
|---------------------|------------------------|------------|  
|Non abilitato|Non specificato|Viene eseguito un popolamento completo dell'indice.|  
|Non abilitato|Specified|L'indice non viene popolato fino a quando non viene eseguita un'istruzione ALTER FULLTEXT INDEX...START POPULATION.|  
|Abilitata|Specified|Viene generato un errore e l'indice non viene modificato.|  
|Abilitata|Non specificato|Viene eseguito un popolamento completo dell'indice.|  
  
 Per ulteriori informazioni sul popolamento di indici full-text, vedere [popolamento degli indici Full-Text](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="changing-the-search-property-list-causes-rebuilding-the-index"></a>La modifica dell'elenco delle proprietà di ricerca richiede la ricompilazione dell'indice  
 La prima volta in cui un indice full-text viene associato a un elenco delle proprietà di ricerca, è necessario ripopolare l'indice per indicizzare i termini di ricerca specifici delle proprietà. I dati dell'indice esistenti non vengono troncati.  
  
 Se tuttavia si associa l'indice full-text a un elenco delle proprietà diverso, l'indice viene ricompilato. La ricompilazione immediata comporta il troncamento dell'indice full-text, ovvero la rimozione di tutti i dati esistenti, e l'indice deve essere ripopolato. Durante il popolamento, le query full-text su tale ricerca tabella di base solo sulle righe della tabella che sono già state indicizzate dal popolamento. I dati dell'indice ripopolato includeranno metadati dalle proprietà registrate dell'elenco delle proprietà di ricerca appena aggiunto.  
  
 Scenari che comportano la ricompilazione includono:  
  
-   Passaggio diretto a un elenco delle proprietà di ricerca diverso (vedere "Scenario A", più avanti in questa sezione).  
  
-   Disattivazione dell'elenco delle proprietà di ricerca e successiva associazione dell'indice a qualsiasi elenco delle proprietà di ricerca (vedere "Scenario B" più avanti in questa sezione)  
  
> [!NOTE]  
>  Per ulteriori informazioni sul funzionamento della ricerca full-text con elenchi delle proprietà di ricerca, vedere [ricerca proprietà dei documenti con elenchi di proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md). Per informazioni sul popolamento completo, vedere [popolamento degli indici Full-Text](../../relational-databases/search/populate-full-text-indexes.md).  
  
### <a name="scenario-a-switching-directly-to-a-different-search-property-list"></a>Scenario A: Passaggio diretto a un elenco delle proprietà di ricerca diverso  
  
1.  Viene creato un indice full-text in `table_1` con un elenco di proprietà di ricerca `spl_1`:  
  
    ```  
    CREATE FULLTEXT INDEX ON table_1 (column_name) KEY INDEX unique_key_index   
       WITH SEARCH PROPERTY LIST=spl_1,   
       CHANGE_TRACKING OFF, NO POPULATION;   
    ```  
  
2.  Viene eseguito un popolamento completo sull'indice full-text:  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1 START FULL POPULATION;  
    ```  
  
3.  L'indice full-text viene associato in seguito a un elenco delle proprietà di ricerca diverso, `spl_2`, utilizzando l'istruzione seguente:  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1 SET SEARCH PROPERTY LIST spl_2;  
    ```  
  
     Questa istruzione comporta un popolamento completo, ovvero il comportamento predefinito.  Tuttavia, prima di avviare questo popolamento, il motore di ricerca full-text tronca automaticamente l'indice.  
  
### <a name="scenario-b-turning-off-the-search-property-list-and-later-associating-the-index-with-any-search-property-list"></a>Scenario B: Disattivazione dell'elenco delle proprietà di ricerca e successiva associazione dell'indice a qualsiasi elenco delle proprietà di ricerca  
  
1.  Viene creato un indice full-text in `table_1` con un elenco di proprietà di ricerca `spl_1`, seguito da un popolamento completo automatico (comportamento predefinito):  
  
    ```  
    CREATE FULLTEXT INDEX ON table_1 (column_name) KEY INDEX unique_key_index   
       WITH SEARCH PROPERTY LIST=spl_1;   
    ```  
  
2.  L'elenco delle proprietà di ricerca viene disattivato, come illustrato di seguito:  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1   
       SET SEARCH PROPERTY LIST OFF WITH NO POPULATION;   
    ```  
  
3.  L'indice full-text è ancora una volta associato allo stesso elenco delle proprietà di ricerca o a uno diverso.  
  
     Ad esempio l'istruzione seguente associa di nuovo l'indice full-text con l'elenco di proprietà di ricerca originale, `spl_1`:  
  
    ```  
    ALTER FULLTEXT INDEX ON table_1 SET SEARCH PROPERTY LIST spl_1;  
    ```  
  
     Questa istruzione avvia un popolamento completo, ovvero il comportamento predefinito.  
  
    > [!NOTE]  
    >  La ricompilazione potrebbe essere necessario anche per un elenco di proprietà di ricerca diverso, ad esempio `spl_2`.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre dell'autorizzazione ALTER sulla tabella o vista indicizzata oppure essere un membro del **sysadmin** ruolo predefinito del server, o **db_ddladmin** o **db_owner** ruoli predefiniti del database .  
  
 Se si specifica SET STOPLIST, l'utente deve disporre dell'autorizzazione REFERENCES per l'elenco di parole non significative. Se si specifica SET SEARCH PROPERTY LIST, l'utente deve disporre dell'autorizzazione REFERENCES per l'elenco delle proprietà di ricerca. Il proprietario dell'elenco di parole non significative o dell'elenco delle proprietà di ricerca specificato può concedere l'autorizzazione REFERENCES, se il proprietario dispone delle autorizzazioni ALTER FULLTEXT CATALOG.  
  
> [!NOTE]  
>  Agli utenti viene concessa l'autorizzazione REFERENCES per l'elenco di parole non significative predefinito fornito con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-setting-manual-change-tracking"></a>A. Impostazione del rilevamento manuale delle modifiche  
 Nell'esempio seguente viene impostato il rilevamento manuale delle modifiche per l'indice full-text nella tabella `JobCandidate`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate  
   SET CHANGE_TRACKING MANUAL;  
GO  
```  
  
### <a name="b-associating-a-property-list-with-a-full-text-index"></a>B. Associazione di un elenco delle proprietà a un indice full-text  
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nell'esempio seguente il `DocumentPropertyList` elenco di proprietà con l'indice full-text di `Production.Document` tabella. Questa istruzione ALTER FULLTEXT INDEX avvia un popolamento completo, che corrisponde al comportamento predefinito della clausola SET SEARCH PROPERTY LIST.  
  
> [!NOTE]  
>  Per un esempio che crea il `DocumentPropertyList` elenco delle proprietà, vedere [CREATE SEARCH PROPERTY LIST &#40; Transact-SQL &#41; ](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST DocumentPropertyList;   
GO  
```  
  
### <a name="c-removing-a-search-property-list"></a>C. Rimozione di un elenco delle proprietà di ricerca  
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nell'esempio seguente viene rimosso l'elenco delle proprietà `DocumentPropertyList` dall'indice full-text della tabella `Production.Document`. In questo esempio non è necessario affrettarsi a rimuovere le proprietà dall'indice, pertanto viene specificata l'opzione WITH NO POPULATION. Tuttavia, la ricerca a livello di proprietà non è più consentita in questo indice full-text.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST OFF WITH NO POPULATION;   
GO  
```  
  
### <a name="d-starting-a-full-population"></a>D. Avvio di un popolamento completo  
 Nell'esempio seguente avvia un popolamento completo nell'indice full-text sul `JobCandidate` tabella.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate   
   START FULL POPULATION;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. fulltext_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)   
 [Popolare gli indici full-text](../../relational-databases/search/populate-full-text-indexes.md)  
  
  

