---
title: CREATE XML INDEX (indici XML selettivi) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1f510151-41d5-45c2-9cd0-b1ca0246fffe
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1ad57508fcfdab112a5ebefc4badb9b65b232444
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853339"
---
# <a name="create-xml-index-selective-xml-indexes"></a>CREATE XML INDEX (indici XML selettivi)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Crea un nuovo indice XML selettivo secondario in un unico percorso già indicizzato da un indice XML selettivo esistente. È inoltre possibile creare indici XML selettivi primari. Per informazioni, vedere [Creare, modificare o eliminare indici XML selettivi](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE XML INDEX index_name  
    ON <table_object> ( xml_column_name )  
    USING XML INDEX sxi_index_name  
    FOR ( <xquery_or_sql_values_path> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<xquery_or_sql_values_path>::=   
<path_name>   
  
<path_name> ::=   
character string literal  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
xmlnamespace_uri AS xmlnamespace_prefix  
  
<index_options> ::=   
(    
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Argomenti  
 *index_name*  
 Nome del nuovo indice che si desidera creare. I nomi degli indici devono essere necessariamente univoci all'interno di una tabella, ma non all'interno di un database. Devono essere anche conformi alle regole degli [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 ON *\<table_object>* Tabella contenente la colonna XML da indicizzare. È possibile usare i formati seguenti:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
 *xml_column_name*  
 Nome della colonna XML contenente il percorso che si desidera indicizzare.  
  
 USING XML INDEX *sxi_index_name*  
 Nome dell'indice XML selettivo esistente.  
  
 FOR **(** \<xquery_or_sql_values_path> **)** Nome del percorso indicizzato in cui creare l'indice XML selettivo secondario. Il percorso che si desidera indicizzare è il nome assegnato dall'istruzione CREATE SELECTIVE XML INDEX. Per altre informazioni, vedere [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
 WITH \<index_options> Per informazioni sulle opzioni di indicizzazione, vedere [CREATE XML INDEX](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>Remarks  
 In ogni colonna XML della tabella di base potrebbero essere presenti più indici XML selettivi secondari.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Prima di poter creare indici XML selettivi secondari in una colonna, è necessario che per tale colonna esista un indice XML selettivo.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER per la tabella o la vista. L'utente deve essere un membro del ruolo predefinito del server **sysadmin** o dei ruoli predefiniti del database **db_ddladmin** e **db_owner** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un indice XML selettivo secondario nel percorso `pathabc`. Il percorso da indicizzare è il nome assegnato dall'istruzione [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
```  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR ( pathabc );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Creare, modificare o eliminare indici XML selettivi secondari](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)  
  
  

