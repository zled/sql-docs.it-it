---
title: Istruzione ALTER INDEX (indici XML selettivi) | Documenti Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: cca96a8f-7737-42d2-bbcc-03d5f858dcc1
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f875f7d34c568bc1156c5f8bce60d893fce8039
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="alter-index-selective-xml-indexes"></a>ALTER INDEX (indici XML selettivi)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Modifica un indice XML selettivo esistente. L'istruzione ALTER INDEX modifica uno o più elementi tra quelli indicati di seguito:  
  
-   Elenco di percorsi indicizzati (clausola FOR).  
  
-   Elenco degli spazi dei nomi (clausola WITH XMLNAMESPACES).  
  
-   Opzioni di indice (clausola WITH).  
  
 Non è possibile modificare indici XML selettivi secondari. Per ulteriori informazioni, vedere [Create, Alter e Drop indici XML selettivi secondari](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER INDEX index_name  
    ON <table_object>   
    [WITH XMLNAMESPACES ( <xmlnamespace_list> )]  
    FOR ( <promoted_node_path_action_list> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
<promoted_node_path_action_list> ::=   
<promoted_node_path_action_item> [, <promoted_node_path_action_list>]  
  
<promoted_node_path_action_item>::=   
<add_node_path_item_action> | <remove_node_path_item_action>  
  
<add_node_path_item_action> ::=  
ADD <path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<remove_node_path_item_action> ::= REMOVE <path_name>   
  
<path_name_or_typed_node_path>::=   
<path_name> | <typed_node_path>  
  
<typed_node_path> ::=   
<node_path> [[AS XQUERY <xsd_type_ext>] | [AS SQL <sql_type>]]  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | 'node()'  
  
<sql_values_node_path_item> ::=   
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type_ext> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::= character_string_literal  
<xml_namespace_prefix> ::= identifier  
  
<index_options> ::=   
(   
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY =OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE =OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Argomenti  
 *index_name*  
 Nome dell'indice esistente che si desidera modificare.  
  
 *\<table_object >*  
 Tabella contenente la colonna XML che si desidera indicizzare. Utilizzare uno dei seguenti formati:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 [WITH XMLNAMESPACES **(** \<xmlnamespace_list > **)**]  
 Elenco degli spazi dei nomi utilizzati nei percorsi da indicizzare. Per informazioni sulla sintassi della clausola WITH XMLNAMESPACES, vedere [WITH XMLNAMESPACES &#40; Transact-SQL &#41; ](../../t-sql/xml/with-xmlnamespaces.md).  
  
 PER **(** \<promoted_node_path_action_list > **)**  
 Elenco dei percorsi indicizzati che si desidera aggiungere o rimuovere.  
  
-   **AGGIUNGERE un percorso.** Per aggiungere un percorso, ricorrere alla stessa sintassi usata per generare percorsi nell'istruzione CREATE SELECTIVE XML INDEX. Per informazioni sui percorsi in cui è possibile specificare nell'istruzione CREATE o ALTER, vedere [specificare percorsi e hint di ottimizzazione per indici XML selettivi](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md).  
  
-   **RIMUOVERE un percorso.** Se si rimuove un percorso, fornire il nome specificato per il percorso in fase di creazione.  
  
 [Con **(** \<index_options > **)**]  
 È possibile specificare solo \<index_options > quando si utilizza ALTER INDEX senza la clausola FOR. Se si utilizza ALTER INDEX per aggiungere o rimuovere percorsi nell'indice, le opzioni dell'indice sono argomenti non validi. Per informazioni sulle opzioni di indice, vedere [CREATE XML INDEX &#40; Indici XML selettivi &#41; ](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>Osservazioni  
  
> [!IMPORTANT]  
>  Se si esegue un'istruzione ALTER INDEX, l'indice XML selettivo viene sempre ricompilato. Considerare l'impatto di questo processo sulle risorse del server.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Per eseguire ALTER INDEX, è necessario disporre dell'autorizzazione ALTER per la tabella o la vista.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata un'istruzione ALTER INDEX. Con questa istruzione il percorso `'/a/b/m'` viene aggiunto alla parte XQuery dell'indice e il percorso `'/a/b/e'` viene eliminato dalla parte SQL dell'indice creato nell'esempio nell'argomento [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md). Il percorso da eliminare viene identificato dal nome fornito al momento della creazione.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
);  
```  
  
 Nell'esempio seguente viene illustrata un'istruzione ALTER INDEX che specifica opzioni di indice. Le opzioni di indice sono consentite poiché l'istruzione non utilizza una clausola FOR per aggiungere o rimuovere percorsi.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
PAD_INDEX = ON;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Creare, modificare ed eliminare indici XML selettivi](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [Specificare percorsi e hint di ottimizzazione per indici XML selettivi](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  
