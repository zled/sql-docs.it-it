---
title: sysmergepartitioninfo (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergepartitioninfo_TSQL
- sysmergepartitioninfo
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepartitioninfo system table
ms.assetid: 7429ad2c-dd33-4f7d-89cc-700e083af518
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2d0c9ed5edb8f143a0e3742a7c49d23d95266640
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergepartitioninfo-transact-sql"></a>sysmergepartitioninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornisce informazioni sulle partizioni per ogni articolo. Contiene una riga per ogni articolo di merge definito nel database locale. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**uniqueidentifier**|Identificatore univoco per l'articolo specificato.|  
|**pubid**|**uniqueidentifier**|Numero di identificazione univoco per la pubblicazione specificata. Viene generato quando si aggiunge la pubblicazione.|  
|**partition_view_id**|**int**|ID della vista di partizione sulla tabella corrente. Nella vista viene riportato il mapping tra ogni riga nell'articolo e l'ID di partizione corrispondente a cui appartiene.|  
|**repl_view_id**|**int**|Da aggiungere.|  
|**partition_deleted_view_rule**|**nvarchar(4000)**|Istruzione SQL utilizzata all'interno di un trigger di replica di tipo merge per recuperare l'ID di partizione per ogni riga eliminata o aggiornata in base ai relativi valori di colonna precedenti.|  
|**partition_inserted_view_rule**|**nvarchar(4000)**|Istruzione SQL utilizzata all'interno di un trigger di replica di tipo merge per recuperare l'ID di partizione per ogni riga inserita o aggiornata in base ai relativi nuovi valori di colonna.|  
|**membership_eval_proc_name**|**sysname**|Il nome della routine che restituisce gli ID di partizione correnti delle righe **MSmerge_contents**.|  
|**column_list**|**nvarchar(4000)**|Elenco separato da virgole delle colonne replicate in un articolo.|  
|**column_list_blob**|**nvarchar(4000)**|Elenco separato da virgole delle colonne replicate in un articolo, comprese le colonne BLOB.|  
|**expand_proc**|**sysname**|Nome della procedura che restituisce nuovamente gli ID di partizione per tutte le righe figlio di una riga padre appena inserita e per le righe padre sottoposte a modifica a livello di partizione oppure che sono state eliminate.|  
|**logical_record_parent_nickname**|**int**|Nome alternativo del padre di livello principale di un articolo specifico in un record logico.|  
|**logical_record_view**|**int**|Vista che ha come output la colonna rowguid dell'articolo padre di livello principale corrispondente a ogni colonna rowguid figlio.|  
|**logical_record_deleted_view_rule**|**nvarchar(4000)**|Simile a **logical_record_view**, ma la mostra le righe figlio nella tabella "eliminata" nei trigger update e delete.|  
|**logical_record_level_conflict_detection**|**bit**|Indica se è necessario rilevare i conflitti a livello di record logico oppure a livello di riga o colonna.<br /><br /> **0** = riga o colonna a livello di rilevamento dei conflitti viene utilizzato.<br /><br /> **1** = logico viene utilizzato il rilevamento dei conflitti record, in cui una modifica in una riga nel server di pubblicazione e modifica in una riga da quella logica record nel sottoscrittore viene gestito come un conflitto.<br /><br /> Quando questo valore è **1**, può essere utilizzata solo la risoluzione dei conflitti a livello di record logico.|  
|**logical_record_level_conflict_resolution**|**bit**|Indica se è necessario risolvere i conflitti a livello di record logico oppure a livello di riga o colonna.<br /><br /> **0** = riga o colonna a livello viene usata la risoluzione.<br /><br /> **1** = In caso di conflitto, l'intero record logico prevalente sovrascrive l'intero record logico nella parte interessata.<br /><br /> Il valore **1** può essere utilizzato con entrambi rilevamento a livello di record logico e con rilevamento a livello di riga o di colonna.|  
|**partition_options**|**tinyint**|Definisce il modo in cui vengono partizionati i dati nell'articolo. Ciò consente di ottimizzare le prestazioni se tutte le righe appartengono a un'unica partizione o a un'unica sottoscrizione. *partition_options* può essere uno dei valori seguenti.<br /><br /> **0** = il filtro dell'articolo è statico oppure non restituisce un subset univoco di dati per ogni partizione, ad esempio una partizione "sovrapposta".<br /><br /> **1** = le partizioni sono sovrapposte e gli aggiornamenti DML apportati nel Sottoscrittore non è possibile modificare la partizione a cui appartiene una riga.<br /><br /> **2** = il filtro dell'articolo restituisce partizioni non sovrapposte, ma più sottoscrittori ricevono la stessa partizione.<br /><br /> **3** = il filtro dell'articolo restituisce partizioni non sovrapposte, univoche per ogni sottoscrizione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
