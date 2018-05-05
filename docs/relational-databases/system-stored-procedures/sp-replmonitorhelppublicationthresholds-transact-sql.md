---
title: sp_replmonitorhelppublicationthresholds (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c77f8e36cc33dfee704ef8f5b945a58c7011a23b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
 [ **@publisher**=] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@publisher_db**=] **'***publisher_db***'**  
 Nome del database pubblicato. *publisher_db* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@publication**=] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@publication_type**=] *publication_type*  
 Tipo di pubblicazione. *publication_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Pubblicazione transazionale.|  
|**1**|Pubblicazione snapshot.|  
|**2**|Pubblicazione di tipo merge.|  
|NULL (predefinito)|La replica tenta di determinare il tipo di pubblicazione.|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|ID della misurazione delle prestazioni di replica. I possibili valori sono i seguenti:<br /><br /> **1expiration** -monitoraggi delle scadenze imminenti delle sottoscrizioni di pubblicazioni transazionali.<br /><br /> **2latency** -monitoraggi delle prestazioni delle sottoscrizioni di pubblicazioni transazionali.<br /><br /> **4mergeexpiration** -monitoraggi delle scadenze imminenti delle sottoscrizioni a pubblicazioni di tipo merge.<br /><br /> **5mergeslowrunduration** -consente di monitorare la durata delle sincronizzazioni di tipo merge attraverso connessioni a larghezza di banda ridotta (Remote).<br /><br /> **6mergefastrunduration** -consente di monitorare la durata delle sincronizzazioni di tipo merge su connessioni a banda larga (LAN).<br /><br /> **7mergefastrunspeed** -controlla la frequenza di sincronizzazione delle sincronizzazioni di tipo merge su connessioni a banda larga (LAN).<br /><br /> **8mergeslowrunspeed** -controlla la frequenza di sincronizzazione delle sincronizzazioni di tipo merge attraverso connessioni a larghezza di banda ridotta (Remote).|  
|**title**|**sysname**|Nome della misurazione delle prestazioni di replica.|  
|**Valore**|**int**|Valore soglia della misurazione delle prestazioni.|  
|**shouldalert**|**bit**|È se deve essere generato un avviso quando la metrica supera la soglia definita per la pubblicazione. il valore **1** indica che deve essere generato un avviso.|  
|**IsEnabled**|**bit**|Se il monitoraggio è abilitato per questa misurazione delle prestazioni di replica per la pubblicazione. il valore **1** indica che il monitoraggio è abilitato.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorhelppublicationthresholds** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **db_owner** o **replmonitor** ruolo predefinito del database nel database di distribuzione possono eseguire **sp_replmonitorhelppublicationthresholds**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
