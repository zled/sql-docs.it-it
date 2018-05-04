---
title: sp_replmonitorhelpmergesession (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 96da0677c94c6d337a428ca9aa612688d33b84ae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spreplmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle sessioni passate per un agente di merge specifico. Viene restituita una riga per ogni sessione che soddisfa i criteri del filtro. Questa stored procedure, utilizzata per il monitoraggio della replica di tipo merge, viene eseguita nel database di distribuzione del server di distribuzione o nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorhelpmergesession [ [ @agent_name = ] 'agent_name' ]  
    [ , [ @hours = ] hours ]  
    [ , [ @session_type = ] session_type ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@agent_name** =] **'***agent_name***'**  
 Nome dell'agente. *agent_name* viene **nvarchar(100)** non prevede alcun valore predefinito.  
  
 [ **@hours** =] *ore*  
 Intervallo di tempo, espresso in ore, per cui vengono restituite informazioni sulle sessioni passate dell'agente. *ore* viene **int**, che può essere uno degli intervalli seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|< **0**|Restituisce informazioni sulle esecuzioni passate dell'agente, per al massimo 100 esecuzioni.|  
|**0** (predefinito)|Restituisce informazioni su tutte le esecuzioni passate dell'agente.|  
|> **0**|Restituisce informazioni sull'agente esecuzioni che si sono verificati negli ultimi *ore* numero di ore.|  
  
 [ **@session_type** =] *session_type*  
 Filtra il set di risultati in base al risultato finale della sessione. *session_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (impostazione predefinita)|Sessioni dell'agente con esito positivo o da ritentare.|  
|**0**|Sessioni dell'agente con esito negativo.|  
  
 [ **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL. Questo parametro viene utilizzato durante l'esecuzione **sp_replmonitorhelpmergesession** nel Sottoscrittore.  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* viene **sysname**, con un valore predefinito è NULL. Questo parametro viene utilizzato durante l'esecuzione **sp_replmonitorhelpmergesession** nel Sottoscrittore.  
  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, con un valore predefinito è NULL. Questo parametro viene utilizzato durante l'esecuzione **sp_replmonitorhelpmergesession** nel Sottoscrittore.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID della sessione del processo dell'agente.|  
|**Stato**|**int**|Stato dell'esecuzione dell'agente:<br /><br /> **1** = avvio<br /><br /> **2** = esito positivo<br /><br /> **3** = in corso<br /><br /> **4** = inattivo<br /><br /> **5** = nuovo tentativo<br /><br /> **6** = esito negativo|  
|**StartTime**|**datetime**|Data e ora di inizio della sessione del processo dell'agente.|  
|**EndTime**|**datetime**|Data e ora di completamento della sessione del processo dell'agente.|  
|**Durata**|**int**|Durata cumulativa, espressa in secondi, della sessione del processo.|  
|**UploadedCommands**|**int**|Numero di comandi caricati durante la sessione dell'agente.|  
|**DownloadedCommands**|**int**|Numero di comandi scaricati durante la sessione dell'agente.|  
|**ErrorMessages**|**int**|Numero di messaggi di errore generati durante la sessione dell'agente.|  
|**ID errore**|**int**|ID dell'errore che si è verificato|  
|**PercentageDone**|**decimal**|Percentuale stimata del numero totale di modifiche già recapitate in una sessione attiva.|  
|**TimeRemaining**|**int**|Numero stimato di secondi rimanenti in una sessione attiva.|  
|**CurrentPhase**|**int**|Fase corrente di una sessione attiva. I possibili valori sono i seguenti.<br /><br /> **1** = caricamento<br /><br /> **2** = download|  
|**LastMessage**|**nvarchar(500)**|Ultimo messaggio registrato dall'agente di merge durante la sessione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorhelpmergesession** consente di monitorare la replica di tipo merge.  
  
 Quando viene eseguito sul server di sottoscrizione, **sp_replmonitorhelpmergesession** solo restituisce informazioni sulle ultime cinque sessioni dell'agente di Merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **db_owner** o **replmonitor** ruolo predefinito del database nel database di distribuzione nel server di distribuzione o nel database di sottoscrizione nel Sottoscrittore possono eseguire **sp _ replmonitorhelpmergesession**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
