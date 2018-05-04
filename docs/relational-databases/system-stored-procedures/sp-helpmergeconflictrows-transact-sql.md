---
title: sp_helpmergeconflictrows (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 60759dfe84d22e919cf14d6fb33454b2d11bae49
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le righe nella tabella dei conflitti specificata. Questa stored procedure viene eseguita nel computer in cui è archiviata la tabella dei conflitti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergeconflictrows [ [ @publication = ] 'publication' ]  
        , [ @conflict_table = ] 'conflict_table'  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publsher_db' ]   
    [ , [ @logical_record_conflicts = ] logical_record_conflicts ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, il valore predefinito è **%**. Se la pubblicazione viene specificata, vengono restituiti tutti i conflitti risultanti corrispondenti. Ad esempio, se il **MSmerge_conflict_Customers** tabella contiene righe in conflitto per il **WA** e **CA** pubblicazioni, passando un nome di pubblicazione **autorità di certificazione**  recupera i conflitti che riguardano il **CA** pubblicazione.  
  
 [  **@conflict_table=**] **'***conflict_table***'**  
 Nome della tabella dei conflitti. *conflict_table* viene **sysname**, non prevede alcun valore predefinito. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, le tabelle dei conflitti vengono denominate usando i nomi di formato con **msmerge_conflict _* pubblicazione *_* articolo * * *, con una tabella per ogni pubblicazione articolo.  
  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 È il nome del database di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@logical_record_conflicts=** ] *logical_record_conflicts*  
 Indica se il set di risultati contiene informazioni sui conflitti a livello di record logici. *logical_record_conflicts* viene **int**, con valore predefinito è 0. **1** indica che vengono restituite le informazioni sui conflitti di record logico.  
  
## <a name="result-sets"></a>Set di risultati  
 **sp_helpmergeconflictrows** , verrà restituito un set costituito la struttura della tabella di base e le colonne aggiuntive.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar(255)**|Origine del conflitto.|  
|**conflict_type**|**int**|Codice che indica il tipo di conflitto:<br /><br /> **1** = conflitto aggiornamento: il conflitto viene rilevato a livello di riga.<br /><br /> **2** = conflitto aggiornamento colonna: il conflitto viene rilevato a livello di colonna.<br /><br /> **3** = conflitto aggiornamento / eliminazione: l'eliminazione prevale nel conflitto.<br /><br /> **4** = aggiornamento prevale il conflitto di eliminazione: rowguid eliminato che perde nel conflitto viene registrato in questa tabella.<br /><br /> **5** = caricare inserimento non riuscito: non è stato possibile applicare l'inserimento dal sottoscrittore nel server di pubblicazione.<br /><br /> **6** = scaricare inserimento non riuscito: l'inserimento dal server di pubblicazione non può essere applicato nel Sottoscrittore.<br /><br /> **7** = caricare eliminazione non riuscita: Impossibile caricare l'eliminazione dal Sottoscrittore al server di pubblicazione.<br /><br /> **8** = scaricare eliminazione non riuscita: Impossibile scaricare l'eliminazione dal server di pubblicazione al sottoscrittore.<br /><br /> **9** = caricare aggiornamento non riuscito: non è stato possibile applicare l'aggiornamento nel Sottoscrittore nel server di pubblicazione.<br /><br /> **10** = download aggiornamento non riuscito: non è stato possibile applicare l'aggiornamento nel server di pubblicazione al sottoscrittore.<br /><br /> **12** = logico Record aggiornamento / eliminazione: il record logico eliminato che perde nel conflitto viene registrato in questa tabella.<br /><br /> **13** = logico Record conflitto aggiornamento/inserimento: inserimento di un record logico è in conflitto con un aggiornamento.<br /><br /> **14** = logico Record conflitto aggiornamento / eliminazione: il record logico aggiornato non prioritario viene registrato in questa tabella.|  
|**reason_code**|**int**|Codice di errore che può essere sensibile al contesto.|  
|**reason_text**|**varchar(720)**|Descrizione dell'errore che può essere sensibile al contesto.|  
|**pubid**|**uniqueidentifier**|Identificatore della pubblicazione.|  
|**MSrepl_create_time**|**datetime**|Ora in cui sono state aggiunte le informazioni sui conflitti.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergeconflictrows** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database e **replmonitor** ruolo nel database di distribuzione può eseguire **sp_helpmergeconflictrows**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare le informazioni sui conflitti per le pubblicazioni di tipo Merge &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
