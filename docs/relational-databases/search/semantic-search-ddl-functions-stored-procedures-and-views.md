---
title: DDL, funzioni, stored procedure e viste di ricerca semantica | Microsoft Docs
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: search
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d55057cc7c145b5c0bf3d6e0263e858164e7747
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>DDL di ricerca semantica, funzioni, stored procedure e viste
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Elenca le istruzioni Transact-SQL e gli oggetti di database che supportano la ricerca semantica statistica in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per l'elenco di istruzioni e oggetti di database che supportano la ricerca full-text, vedere [DDL di ricerca full-text, funzioni, stored procedure e viste](../../relational-databases/search/full-text-search-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="ddl"></a> Istruzioni DDL (Data Definition Language)  
  
|Oggetto|Ulteriori informazioni|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)|[Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)|[Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="func"></a> Funzioni di sistema  
  
|Oggetto|Ulteriori informazioni|  
|------------|----------------------|  
|[semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)|[Trovare frasi chiave nei documenti mediante ricerca semantica](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)|[Trovare documenti simili e correlati tramite la ricerca semantica](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)|[Trovare documenti simili e correlati tramite la ricerca semantica](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="meta"></a> Funzioni per i metadati di sistema  
  
|Oggetto|Ulteriori informazioni|  
|------------|----------------------|  
|[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)|[Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)|[Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|[Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)|[Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)|[Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)|[Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="sproc"></a> Stored procedure di sistema  
  
|Oggetto|Ulteriori informazioni|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md)|[Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md)|[Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="cv"></a> Viste del catalogo  
  
|Oggetto|Ulteriori informazioni|  
|------------|----------------------|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|[Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)|[Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)|[Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="dmv"></a> DMV  
  
|Oggetto|Ulteriori informazioni|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)|[Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|[Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)|[Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
