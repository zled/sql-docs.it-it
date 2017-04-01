---
title: "Configurazione e gestione di word breaker e stemmer per la ricerca | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "lingue [ricerca full-text]"
  - "ricerca full-text [SQL Server], stemmer"
  - "analisi linguistica [ricerca full-text]"
  - "indici full-text [SQL Server], analisi linguistica"
  - "ricerca full-text [SQL Server], word breaker"
  - "default full-text language - opzione"
  - "stemmer [ricerca full-text]"
  - "coniugazione di verbi [ricerca full-text]"
  - "word breaker [ricerca full-text]"
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
caps.latest.revision: 89
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 88
---
# Configurazione e gestione di word breaker e stemmer per la ricerca
  Word breaker e stemmer eseguono l'analisi linguistica su tutti i dati con indicizzazione full-text. L'analisi linguistica riguarda la ricerca dell'inizio e della fine delle parole (isolamento delle parole) e la coniugazione dei verbi (flessione). Word breaker e stemmer sono specifici della lingua e le regole per l'analisi linguistica variano a seconda della lingua. Un *word breaker* identifica singole parole determinando i delimitatori di parola in base alle regole lessicali della lingua. Ogni parola (*token*) viene inserita nell'indice full-text utilizzando una rappresentazione compressa per ridurre le relative dimensioni. Lo *stemmer* genera forme flessive di una particolare parola in base alle regole di quella lingua, ad esempio "running", "ran" e "runner" sono varie forme della parola "run".  
  
 L'utilizzo di word breaker specifici di ogni lingua consente una maggiore accuratezza dei termini risultanti per le diverse lingue. Se è disponibile un word breaker per la famiglia linguistica, ma non per una specifica lingua secondaria, viene utilizzata la lingua principale. Il word breaker francese viene ad esempio utilizzato anche per la gestione di testo redatto in francese canadese. Se per una particolare lingua non sono disponibili word breaker, verrà utilizzato il word breaker della lingua neutra. Con il word breaker della lingua neutra, le parole vengono spezzate in corrispondenza di caratteri neutri, ad esempio spazi e segni di punteggiatura.  
  
##  <a name="register"></a> Registrazione di word breaker  
 Per potere utilizzare i word breaker di una determinata lingua, è necessario registrarli. Per i word breaker registrati, anche le risorse linguistiche associate, ovvero stemmer, parole non significative e thesaurus, risultano disponibili per le operazioni di indicizzazione e query full-text. Per visualizzare un elenco delle lingue i cui word breaker sono attualmente registrati con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
 SELECT * FROM sys.fulltext_languages  
  
 Se si aggiunge, rimuove o modifica un word breaker, è necessario aggiornare l'elenco degli identificatori delle impostazioni locali (LCID) di Microsoft Windows supportati per l'indicizzazione e le query full-text. Per altre informazioni, vedere [View or Change Registered Filters and Word Breakers](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md).  
  
##  <a name="default"></a> Impostazione dell'opzione relativa alla lingua predefinita full-text  
 Per una versione localizzata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'opzione della **lingua predefinita full-text** viene impostata dal programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sulla lingua del server, se esiste una corrispondenza appropriata. Per le versioni non localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'opzione **default full-text language** è impostata sull'inglese.  
  
 Quando si crea o modifica un indice full-text, è possibile specificare una lingua diversa per ogni colonna di indicizzazione full-text. Se per una colonna non è stata specificata alcuna lingua, il valore predefinito è quello dell'opzione di configurazione **default full-text language**.  
  
> [!NOTE]  
>  È necessario che a tutte le colonne elencate in una singola clausola di funzione per query full-text venga applicata la stessa lingua, a meno che nella query l'opzione LANGUAGE non sia specificata. La lingua utilizzata per la colonna indicizzata full-text oggetto della query determina l'analisi linguistica eseguita sugli argomenti dei predicati ([CONTAINS](../../t-sql/queries/contains-transact-sql.md) e [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)) e delle funzioni ([CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) e [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md)) delle query full-text.  
  
##  <a name="lang"></a> Scelta della lingua per una colonna indicizzata  
 Quando si crea un indice full-text, è consigliabile specificare una lingua per ogni colonna indicizzata. Se non viene specificata alcuna lingua per una colonna, viene utilizzata quella predefinita di sistema. La lingua di una colonna determina il word breaker e lo stemmer utilizzati per l'indicizzazione di quella colonna. Anche il file del thesaurus di quella lingua verrà utilizzato dalle query full-text sulla colonna.  
  
 Quando si crea un indice full-text, è necessario considerare alcuni aspetti relativi alla scelta della lingua delle colonne. Tali considerazioni riguardano il modo in cui il testo viene suddiviso in token e quindi indicizzato dal motore di ricerca full-text. Per altre informazioni, vedere [Scelta di una lingua durante la creazione di un indice full-text](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  
  
 **Per visualizzare la lingua del word breaker di una colonna**  
  
-   [Gestione di indici full-text.](../Topic/Manage%20Full-Text%20Indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="info"></a> Come ottenere informazioni sui word breaker  
 **Visualizzazione del risultato della suddivisione in token di una combinazione di word breaker, thesaurus ed elenco di parole non significative**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md).  
  
 **Per restituire informazioni sui word breaker registrati**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
  
##  <a name="tshoot"></a> Risoluzione dei problemi relativi agli errori di timeout del word breaking  
 Un errore di timeout del word breaking potrebbe verificarsi in diverse situazioni. Per informazioni su queste situazioni e su come rispondere, vedere [MSSQLSERVER_30053](../Topic/MSSQLSERVER_30053.md).  
  
##  <a name="impact"></a> Informazioni sull'impatto dei nuovi word breaker  
 Ogni versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include in genere nuovi word breaker con regole linguistiche migliori e maggiore accuratezza rispetto alle versioni precedenti. È possibile che il comportamento dei nuovi word breaker sia leggermente diverso da quello dei word breaker negli indici full-text importati da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo aspetto è rilevante se si importa un catalogo full-text al momento dell'aggiornamento di un database alla versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Una o più lingue utilizzate dagli indici full-text nel catalogo full-text potrebbero essere associate ai nuovi word breaker. Per altre informazioni, vedere [Aggiornamento della ricerca full-text](../../relational-databases/search/upgrade-full-text-search.md).  
  
 Per un elenco completo di tutti i word breaker, vedere [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
  
## Vedere anche  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)   
 [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Aggiornamento della ricerca full-text](../../relational-databases/search/upgrade-full-text-search.md)  
  
  