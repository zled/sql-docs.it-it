---
title: sys.dm_fts_index_keywords (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 687a81711efdaf98f142a0d314db94a53cc74371
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsindexkeywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sul contenuto di un indice full-text per la tabella specificata.  
  
 **Sys.dm fts_index_keywords** è una funzione a gestione dinamica.  
  
> [!NOTE]  
>  Per visualizzare informazioni sugli indici full-text di livello inferiore, utilizzare il [Sys.dm fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md) funzione a gestione dinamica a livello di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>Argomenti  
 db_id('*database_name*')  
 Una chiamata al [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md) (funzione). Questa funzione accetta un nome di database e restituisce l'ID del database cui **Sys.dm fts_index_keywords** utilizza per individuare il database specificato. Se *database_name* viene omesso, viene restituito l'ID del database corrente.  
  
 object_id('*table_name*')  
 Una chiamata al [object_id ()](../../t-sql/functions/object-id-transact-sql.md) (funzione). Tale funzione accetta un nome di tabella e restituisce l'ID della tabella che contiene l'indice full-text da controllare.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**keyword**|**nvarchar(4000)**|Rappresentazione esadecimale della parola chiave archiviata nell'indice full-text.<br /><br /> Nota: OxFF rappresenta il carattere speciale che indica la fine di un file o un set di dati.|  
|**display_term**|**nvarchar(4000)**|Formato leggibile della parola chiave derivato dal formato esadecimale.<br /><br /> Nota: Il **display_term** valore per OxFF è "Fine del FILE".|  
|**column_id**|**int**|ID della colonna utilizzata per eseguire l'indicizzazione full-text della parola chiave corrente.|  
|**document_count**|**int**|Numero di documenti o righe che contengono il termine corrente.|  
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni restituite da **Sys.dm fts_index_keywords** è utile per individuare, tra le altre cose, i seguenti:  
  
-   Appartenenza di una parola chiave all'indice full-text.  
  
-   Numero di documenti o righe che contengono una parola chiave specificata.  
  
-   Parola chiave più comune nell'indice full-text:  
  
    -   **document_count** di ogni *keyword_value* rispetto al totale **document_count**, il numero di documenti di 0xFF.  
  
    -   In genere è più appropriato definire come parole non significative le parole chiave più comuni.  
  
> [!NOTE]  
>  Il **document_count** restituito da **Sys.dm fts_index_keywords** può essere meno preciso per un documento specifico rispetto al conteggio restituito da **Sys.dm fts_index_keywords_by_document** o **CONTAINS** query. Questa possibile imprecisione è stimata essere minore dell'1%. Questo può verificarsi in quanto un **document_id** possono essere conteggiati due volte se si ripete in più di una riga nel frammento di indice, o se viene visualizzato più volte nella stessa riga. Per ottenere un conteggio più preciso per un documento specifico, utilizzare **Sys.dm fts_index_keywords_by_document** o **CONTAINS** query.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. Visualizzazione del contenuto dell'indice full-text di alto livello  
 Nell'esempio seguente vengono visualizzate informazioni sul contenuto di alto livello dell'indice full-text nella tabella `HumanResources.JobCandidate`.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca full-Text e funzioni e viste a gestione dinamica della ricerca semantica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Ricerca full-Text](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
