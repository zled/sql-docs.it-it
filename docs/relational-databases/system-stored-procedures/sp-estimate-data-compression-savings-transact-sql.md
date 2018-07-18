---
title: sp_estimate_data_compression_savings (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs:
- TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 25798372f2b949446b746164665dbfe6752443d7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260584"
---
# <a name="spestimatedatacompressionsavings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le dimensioni correnti degli oggetti richiesti e stima le dimensioni dell'oggetto per lo stato di compressione richiesto. La compressione può essere valutata per intere tabelle o parti di esse, inclusi heap, indici cluster, indici non cluster, viste indicizzate e partizioni di tabella e di indice. Gli oggetti possono essere compressi utilizzando la compressione di riga o di pagina. Se la tabella, la partizione o l'indice è già compresso, è possibile utilizzare questa procedura per stimare le dimensioni della tabella, della partizione o dell'indice se venisse ricompresso.  
  
> [!NOTE]  
>  La compressione e **sp_estimate_data_compression_savings** non sono disponibili in ogni edizione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Per stimare le dimensioni dell'oggetto in caso di applicazione dell'impostazione di compressione richiesta, questa stored procedure esegue il campionamento dell'oggetto di origine e carica i relativi dati in una tabella e in un indice equivalenti creati in tempdb. La tabella o l'indice creato in tempdb viene quindi compresso in base all'impostazione richiesta e viene calcolato il risparmio stimato in caso di utilizzo della compressione.  
  
 Per modificare lo stato di compressione di una tabella, indice o partizione, utilizzare il [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) o [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) istruzioni. Per informazioni generali sulla compressione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
> [!NOTE]  
>  Se i dati esistenti sono frammentati, potrebbe essere possibile ridurne le dimensioni senza utilizzare la compressione ricompilando l'indice. Per gli indici, il fattore di riempimento viene applicato durante la ricompilazione. Questo potrebbe comportare un aumento delle dimensioni dell'indice.  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [@index_id = ] index_id   
   , [@partition_number = ] partition_number   
   , [@data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @schema_name=] '*schema_name*'  
 Nome dello schema del database che contiene la tabella o la vista indicizzata. *schema_name* viene **sysname**. Se *schema_name* è NULL, viene utilizzato lo schema predefinito dell'utente corrente.  
  
 [ @object_name=] '*object_name*'  
 Nome della tabella o della vista indicizzata su cui è basato l'indice. *object_name* è di tipo **sysname**.  
  
 [ @index_id=] '*index_id*'  
 ID dell'indice. *index_id* viene **int**, e può essere uno dei seguenti valori: il numero di ID di un indice, NULL o 0 se *object_id* è un heap. Per restituire informazioni per tutti gli indici per una tabella di base o una vista, specificare NULL. Se si specifica NULL, è necessario specificare NULL anche per *numero_partizione*.  
  
 [ @partition_number=] '*numero_partizione*'  
 Numero di partizione nell'oggetto. *partition_number* viene **int**, e può essere uno dei seguenti valori: il numero di partizione di un indice o heap, NULL o 1 per un heap o un indice non partizionato.  
  
 Per specificare la partizione, è inoltre possibile specificare il [$partition](../../t-sql/functions/partition-transact-sql.md) (funzione). Per restituire le informazioni per tutte le partizioni dell'oggetto, specificare NULL.  
  
 [ @data_compression=] '*data_compression*'  
 Tipo di compressione da valutare. *DATA_COMPRESSION* può essere uno dei seguenti valori: NONE, ROW o PAGE.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Per offrire informazioni sulle dimensioni correnti e stimate della tabella, dell'indice o della partizione, viene restituito il set di risultati seguente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|Nome della tabella o della vista indicizzata.|  
|schema_name|**sysname**|Schema della tabella o della vista indicizzata.|  
|index_id|**int**|ID di un indice:<br /><br /> 0 = heap<br /><br /> 1 = indice cluster<br /><br /> > 1 = Indice non cluster|  
|partition_number|**int**|Numero di partizioni. Per una tabella o un indice non partizionato viene restituito 1.|  
|size_with_current_compression_setting (KB)|**bigint**|Dimensioni attuali della tabella, della partizione o dell'indice richiesto.|  
|size_with_requested_compression_setting (KB)|**bigint**|Dimensioni stimate della tabella, della partizione o dell'indice in caso di utilizzo dell'impostazione di compressione richiesta e, se applicabile, del fattore di riempimento esistente e presupponendo che non vi sia frammentazione.|  
|sample_size_with_current_compression_setting (KB)|**bigint**|Dimensioni del campione con l'impostazione di compressione corrente. È inclusa qualsiasi frammentazione.|  
|sample_size_with_requested_compression_setting (KB)|**bigint**|Dimensioni del campione creato utilizzando l'impostazione di compressione richiesta e, se applicabile, il fattore di riempimento esistente e senza frammentazione.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare sp_estimate_data_compression_savings per stimare il risparmio che è possibile ottenere abilitando la compressione di riga o di pagina per una tabella o una partizione. Se, ad esempio, le dimensioni medie della riga possono essere ridotte del 40%, è possibile ridurre del 40% le dimensioni dell'oggetto. Si potrebbe non ottenere un risparmio in termini di spazio a seconda del fattore di riempimento e delle dimensioni della riga. Se si riducono del 40% le dimensioni di una riga lunga 8000 byte, ad esempio, una pagina di dati può comunque contenere una sola riga e non si ottiene alcun risparmio.  
  
 Se i risultati dell'esecuzione di sp_estimate_data_compression_savings indicano un aumento delle dimensioni della tabella, significa che in molte righe della tabella viene utilizzata quasi la precisione completa dei tipi di dati e l'aggiunta del limitato overhead necessario per il formato compresso supera il risparmio che è possibile ottenere dalla compressione. In questi rari casi, non abilitare la compressione.  
  
 Se per una tabella è abilitata la compressione, utilizzare sp_estimate_data_compression_savings per stimare le dimensioni medie della riga nel caso in cui la tabella non fosse compressa.  
  
 Durante questa operazione viene acquisito un blocco (IS) nella tabella. Se non è possibile ottenere un blocco (IS), la procedura viene bloccata. La tabella viene analizzata con il livello di isolamento Read committed.  
  
 Se l'impostazione di compressione richiesta corrisponde all'impostazione di compressione corrente, la stored procedure restituirà le dimensioni stimate senza frammentazione dei dati e utilizzando il fattore di riempimento esistente.  
  
 Se l'ID della partizione o dell'indice non esiste, non viene restituito alcun risultato.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per la tabella.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Questa procedura non si applica alle tabelle columnstore, pertanto non accetta i parametri di compressione dei dati COLUMNSTORE_ARCHIVE e COLUMNSTORE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono stimate le dimensioni della tabella `Production.WorkOrderRouting` in caso di utilizzo della compressione `ROW`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Implementazione della compressione Unicode](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
