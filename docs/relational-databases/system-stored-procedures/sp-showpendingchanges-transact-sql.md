---
title: sp_showpendingchanges (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords: sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a80816191ac9ad2cd9a210c59268b23f4ea3a093
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spshowpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di risultati che mostra le modifiche in attesa di replicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione e nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!NOTE]  
>  Questa procedura consente di ottenere un'approssimazione del numero di modifiche e delle righe interessate da tali modifiche, recuperando ad esempio informazioni dal Server di pubblicazione o dal Sottoscrittore, ma non da entrambi contemporaneamente. Le informazioni archiviate nell'altro nodo potrebbero produrre un set di modifiche più piccolo da sincronizzare rispetto alle stime della procedura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_showpendingchanges [ [ @destination_server = ] 'destination_server' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article']  
    [ , [ @show_rows = ] show_rows]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @destination_server  **=**  ] **'***destination_server***'**  
 Nome del server a cui vengono applicate le modifiche replicate. *destination_server* è **sysname**, il valore predefinito NULL.  
  
 [ @publication  **=**  ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, con un valore predefinito null. Quando *pubblicazione* viene specificato, i risultati sono limitati solo per la pubblicazione specificata.  
  
 [ @article  **=**  ] **'***articolo***'**  
 Nome dell'articolo. *articolo* è **sysname**, con un valore predefinito null. Quando *articolo* viene specificato, i risultati sono limitati solo per l'articolo specificato.  
  
 [ @show_rows  **=**  ] *show_rows*  
 Specifica se il set di risultati contiene informazioni più specifiche sulle modifiche in sospeso, con un valore predefinito di **0**. Se un valore di **1** è specificato, il set di risultati contiene le colonne is_delete e rowguid.  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|Nome del server nel quale è in corso la replica delle modifiche.|  
|pub_name|**sysname**|Nome della pubblicazione.|  
|destination_db_name|**sysname**|Nome del database nel quale è in corso la replica delle modifiche.|  
|is_dest_subscriber|**bit**|Indica che è in corso la replica delle modifiche in un Sottoscrittore. Il valore **1** indica che le modifiche vengono replicate in un sottoscrittore. **0** significa che le modifiche vengano replicate in un server di pubblicazione.|  
|article_name|**sysname**|Nome dell'articolo nella tabella di origine delle modifiche.|  
|pending_deletes|**int**|Numero di eliminazioni in attesa della replica.|  
|pending_ins_and_upd|**int**|Numero di inserimenti e aggiornamenti in attesa della replica.|  
|is_delete|**bit**|Indica se la modifica in sospeso è un'eliminazione. Il valore **1** indica che la modifica è un'operazione di eliminazione. Richiede un valore di **1** per @show_rows.|  
|rowguid|**uniqueidentifier**|GUID che identifica la riga modificata. Richiede un valore di **1** per @show_rows.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 La stored procedure sp_showpendingchanges viene utilizzata per la replica di tipo merge.  
  
 sp_showpendingchanges viene utilizzata quando la risoluzione dei problemi di replica di tipo merge.  
  
 Il risultato della stored procedure sp_showpendingchanges non include righe di generazione 0.  
  
 Se un articolo specificato per *articolo* non appartiene alla pubblicazione specificata per *pubblicazione* viene restituito un conteggio pari a 0 per pending_deletes e pending_ins_and_upd.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del ruolo predefinito del server sysadmin o del ruolo predefinito del database db_owner possono eseguire sp_showpendingchanges.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
