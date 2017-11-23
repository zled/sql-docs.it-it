---
title: sp_replmonitorhelppublicationthresholds (Transact-SQL) | Documenti Microsoft
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
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords: sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 62f7770bb8127beba19170a6ee60369f83a11c02
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spreplmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le metriche relative alle soglie impostate per una pubblicazione monitorata. Questa stored procedure, utilizzata per il monitoraggio della replica, viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorhelppublicationthresholds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db** =] **'***publisher_db***'**  
 Nome del database pubblicato. *publisher_db* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publication_type** =] *publication_type*  
 Tipo di pubblicazione. *publication_type* è **int**, i possibili valori sono i seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**0**|Pubblicazione transazionale.|  
|**1**|Pubblicazione snapshot.|  
|**2**|Pubblicazione di tipo merge.|  
|NULL (predefinito)|La replica tenta di determinare il tipo di pubblicazione.|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|ID della misurazione delle prestazioni di replica. I possibili valori sono i seguenti:<br /><br /> **1expiration** -esegue il monitoraggio delle scadenze imminenti delle sottoscrizioni di pubblicazioni transazionali.<br /><br /> **2latency** -esegue il monitoraggio delle prestazioni delle sottoscrizioni di pubblicazioni transazionali.<br /><br /> **4mergeexpiration** -esegue il monitoraggio delle scadenze imminenti delle sottoscrizioni di pubblicazioni di tipo merge.<br /><br /> **5mergeslowrunduration** -controlla la durata delle sincronizzazioni di tipo merge attraverso connessioni a larghezza di banda ridotta (remoto).<br /><br /> **6mergefastrunduration** -controlla la durata delle sincronizzazioni di tipo merge su connessioni a banda larga (LAN).<br /><br /> **7mergefastrunspeed** -controlla la frequenza di sincronizzazione delle sincronizzazioni di tipo merge su connessioni a banda larga (LAN).<br /><br /> **8mergeslowrunspeed** -controlla la frequenza di sincronizzazione delle sincronizzazioni di tipo merge attraverso connessioni a larghezza di banda ridotta (remoto).|  
|**title**|**sysname**|Nome della misurazione delle prestazioni di replica.|  
|**valore**|**int**|Valore soglia della misurazione delle prestazioni.|  
|**shouldalert**|**bit**|È se deve essere generato un avviso quando la metrica supera la soglia definita per la pubblicazione. il valore **1** indica che deve essere generato un avviso.|  
|**IsEnabled**|**bit**|Se il monitoraggio è abilitato per questa misurazione delle prestazioni di replica per la pubblicazione. il valore **1** indica che il monitoraggio è abilitato.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorhelppublicationthresholds** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **db_owner** o **replmonitor** ruolo predefinito del database nel database di distribuzione possono eseguire **sp_replmonitorhelppublicationthresholds**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
