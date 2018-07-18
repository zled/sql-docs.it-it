---
title: sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Documenti Microsoft
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
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3d76b4c7001f946ad01836c36982d81f90df397c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni dettagliate a livello di articolo su una specifica sessione di replica dell'agente di merge, utilizzato per monitorare la replica di tipo merge. Il set di risultati include una riga di dettaglio per ogni articolo sincronizzato durante la sessione, nonché una riga che rappresenta l'inizializzazione della sessione e righe che riepilogano le fasi di caricamento e scaricamento della sessione. Questa stored procedure viene eseguita nel database di distribuzione del server di distribuzione oppure nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@session_id** = ] *session_id*  
 Specifica una sessione dell'agente. *session_id* viene **int** non prevede alcun valore predefinito.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Fase della sessione di sincronizzazione. I possibili valori sono i seguenti.<br /><br /> **0** = inizializzazione riga o riepilogo<br /><br /> **1** = caricamento<br /><br /> **2** = download|  
|**ArticleName**|**sysname**|Nome dell'articolo in fase di sincronizzazione. **ArticleName** contiene anche le informazioni di riepilogo per le righe nel set di risultati che non rappresentano dettagli degli articoli.|  
|**PercentComplete**|**decimal**|Indica la percentuale delle modifiche totali applicate in una riga di dettaglio dell'articolo per le sessioni in esecuzione e quelle non riuscite.|  
|**RelativeCost**|**decimal**|Indica il tempo dedicato alla sincronizzazione dell'articolo come percentuale del tempo totale di sincronizzazione per la sessione.|  
|**Durata**|**int**|Durata della sessione dell'agente.|  
|**Inserts**|**int**|Numero di inserimenti in una sessione.|  
|**Aggiornamenti**|**int**|Numero di aggiornamenti in una sessione.|  
|**Eliminazioni**|**int**|Numero di eliminazioni in una sessione.|  
|**Conflitti**|**int**|Numero di conflitti verificatisi in una sessione.|  
|**ID errore**|**int**|ID di un errore di sessione.|  
|**Seqno non**|**int**|Ordine delle sessioni nel set di risultati.|  
|**RowType**|**int**|Indica il tipo di informazioni rappresentato da ogni riga nel set di risultati.<br /><br /> **0** = inizializzazione<br /><br /> **1** = riepilogo del caricamento<br /><br /> **2** = dettagli di caricamento dell'articolo<br /><br /> **3** = riepilogo del download<br /><br /> **4** = dettagli di scaricamento dell'articolo|  
|**Modifiche allo schema**|**int**|Numero di modifiche dello schema in una sessione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorhelpmergesessiondetail** consente di monitorare la replica di tipo merge.  
  
 Quando viene eseguito sul server di sottoscrizione, **sp_replmonitorhelpmergesessiondetail** solo restituisce informazioni dettagliate sulle ultime 5 sessioni dell'agente di Merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **db_owner** o **replmonitor** ruolo predefinito del database nel database di distribuzione nel server di distribuzione o nel database di sottoscrizione nel Sottoscrittore possono eseguire **sp _ replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
