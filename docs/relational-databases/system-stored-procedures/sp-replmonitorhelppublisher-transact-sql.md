---
title: sp_replmonitorhelppublisher (Transact-SQL) | Documenti Microsoft
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
- sp_replmonitorhelppublisher_TSQL
- sp_replmonitorhelppublisher
helpviewer_keywords:
- sp_replmonitorhelppublisher
ms.assetid: 171501fe-4b74-4647-96c3-7691c777e01b
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2235b36a6ad5c78466162d071b073368e455cabe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spreplmonitorhelppublisher-transact-sql"></a>sp_replmonitorhelppublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sullo stato corrente per uno o più server di pubblicazione associati a un server di distribuzione. Questa stored procedure, utilizzata per il monitoraggio della replica, viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorhelppublisher [ [ @publisher = ] 'publisher' ]  
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione di cui viene monitorato lo stato. *server di pubblicazione* viene **sysname**, con valore predefinito è NULL. Se NULL, verranno restituite informazioni per tutti i server di pubblicazione che utilizzano il server di distribuzione.  
  
 [  **@refreshpolicy=** ] *refreshpolicy*  
 Solo per uso interno.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**distribution_db**|**sysname**|Nome del database di distribuzione utilizzato dal server di pubblicazione specificato.|  
|**status**|**int**|Stato massimo di tutti gli agenti di replica associati alle pubblicazioni nel server di pubblicazione specificato. I possibili valori sono i seguenti:<br /><br /> **1** = avviato<br /><br /> **2** = ha avuto esito positivo<br /><br /> **3** = in corso<br /><br /> **4** = inattivo<br /><br /> **5** = nuovo tentativo in corso<br /><br /> **6** = non è riuscita|  
|**Avviso**|**int**|Avviso correlato alla soglia massima generata da una sottoscrizione appartenente a una pubblicazione nel server di pubblicazione specificato. Può essere il risultato di un'operazione OR logica su uno o più dei valori seguenti.<br /><br /> **1** = expiration-una sottoscrizione di una pubblicazione transazionale non è stata sincronizzata entro il valore soglia periodo di memorizzazione.<br /><br /> **2** = latency - il tempo necessario per replicare i dati da un server di pubblicazione transazionale al sottoscrittore supera la soglia, espresso in secondi.<br /><br /> **4** = mergeexpiration - una sottoscrizione di una pubblicazione di tipo merge non è stata sincronizzata entro il valore soglia periodo di memorizzazione.<br /><br /> **8** = mergefastrunduration - il tempo impiegato per completare la sincronizzazione di una sottoscrizione di tipo merge supera la soglia, espresso in secondi, su una connessione di rete veloce.<br /><br /> **16** = mergeslowrunduration - il tempo impiegato per completare la sincronizzazione di una sottoscrizione di tipo merge supera la soglia, espresso in secondi, su una connessione di rete lenta o remota.<br /><br /> **32** = mergefastrunspeed – la velocità di recapito delle righe durante la sincronizzazione di una sottoscrizione di tipo merge è minore della soglia, in righe al secondo, su una connessione di rete veloce.<br /><br /> **64** = mergeslowrunspeed – la velocità di recapito delle righe durante la sincronizzazione di una sottoscrizione di tipo merge è minore della soglia, in righe al secondo, su una connessione di rete lenta o remota.|  
|**publicationcount**|**int**|Numero di pubblicazioni appartenenti al server di pubblicazione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorhelppublisher** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** al server di distribuzione o i membri del ruolo predefinito del server di **db_owner** o **replmonitor** possono ruoli predefiniti del database nel database di distribuzione eseguire **sp_replmonitorhelppublisher**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
