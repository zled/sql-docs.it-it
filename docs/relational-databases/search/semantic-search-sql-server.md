---
title: Ricerca semantica (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 287ef0015b58e65e541ded8bc1a4200fed804814
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755969"
---
# <a name="semantic-search-sql-server"></a>Ricerca semantica (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
La ricerca semantica statistica offre una visione approfondita dei documenti non strutturati archiviati in database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite l'estrazione e l'indicizzazione di *frasi chiave*statisticamente pertinenti. Le frasi chiave vengono quindi usate per identificare e indicizzare *documenti simili o correlati*.  
  
##  <a name="whatcanido"></a> Funzionalità della ricerca semantica  
 La ricerca semantica è basata sulla caratteristica di ricerca full-text esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma consente nuovi scenari che vanno oltre le ricerche di parole chiave. Mentre la ricerca full-text consente di eseguire query sulle *parole* in un documento, la ricerca semantica consente di eseguire query sul *significato* del documento. Esempi di soluzioni ora possibili includono l'estrazione automatica dei tag, l'individuazione di contenuto correlato e la navigazione gerarchica in contenuto simile. Ad esempio, è possibile eseguire una query sull'indice di frasi chiave per compilare la tassonomia per un'organizzazione o per una raccolta di documenti. In alternativa, è possibile eseguire una query sull'indice di somiglianza dei documenti per identificare i curriculum che corrispondono a un'offerta di lavoro.  
  
 Negli esempi seguenti vengono illustrate le capacità della ricerca semantica. Questi esempi illustrato allo stesso tempo le tre funzioni di set di righe Transact-SQL usate per recuperare gli indici semantici e ottenere i risultati in forma di dati strutturati.  
  
###  <a name="find1"></a> Find the key phrases in a document  
 Nella query seguente vengono ottenute le frasi chiave identificate nel documento di esempio. Presenta i risultati in ordine decrescente in base al punteggio di classificazione della rilevanza statistica di ogni frase chiave.
 
 Questa query chiama la funzione [semantickeyphrasetable](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
###  <a name="find2"></a> Find similar or related documents  
 Nella query seguente vengono ottenuti i documenti identificati come simili o correlati al documento di esempio. Presenta i risultati in ordine decrescente in base al punteggio di classificazione della somiglianza dei due documenti.
 
 Questa query chiama la funzione [semanticsimilaritytable](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
###  <a name="find3"></a> Find the key phrases that make documents similar or related  
 Nella query seguente vengono ottenute le frasi chiavi indicanti la somiglianza o la correlazione tra i due documenti di esempio. Presenta i risultati in ordine decrescente in base al punteggio di classificazione del peso di ogni frase chiave.
 
 Questa query chiama la funzione [semanticsimilaritydetailstable](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
##  <a name="store"></a> Archiviare i documenti in SQL Server  
 Per poter indicizzare documenti con la ricerca semantica, è necessario archiviarli in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La funzionalità FileTable in SQL Server consente di inserire file e documenti non strutturati nel database relazionale. Di conseguenza, gli sviluppatori di database possono modificare documenti insieme a dati strutturati in operazioni basate su set Transact-SQL.  
  
 Per altre informazioni sulla funzionalità FileTable, vedere [FileTable &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md). Per informazioni sulla funzionalità FILESTREAM, ovvero un'altra opzione per l'archiviazione di documenti nel database, vedere [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
##  <a name="reltasks"></a> Related tasks  
 [Installare e configurare la ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)  
 Vengono descritti i prerequisiti per la ricerca semantica statistica e viene indicato come installarli o verificarli.  
  
 [Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)  
 Viene descritto come abilitare o disabilitare l'indicizzazione semantica statistica in colonne selezionate contenenti documenti o testo.  
  
 [Trovare frasi chiave nei documenti mediante ricerca semantica](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)  
 Viene descritto come individuare le frasi chiave nei documenti o nelle colonne di testo configurati per l'indicizzazione semantica statistica.  
  
 [Trovare documenti simili e correlati tramite la ricerca semantica](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)  
 Viene descritto come reperire documenti o valori di testo simili o correlati, nonché informazioni relative alla somiglianza o correlazione, in colonne configurate per l'indicizzazione semantica statistica.  
  
 [Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
 Vengono descritti il processo di indicizzazione semantica e le attività correlate al monitoraggio e alla gestione degli indici.  
  
##  <a name="relcontent"></a> Related content  
 [DDL di ricerca semantica, funzioni, stored procedure e viste](../../relational-databases/search/semantic-search-ddl-functions-stored-procedures-and-views.md)  
 Sono elencati le istruzioni Transact-SQL e gli oggetti di database di SQL Server aggiunti o modificati per supportare la ricerca semantica statistica.  
  
  
