---
title: MSpublications (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSpublications
- MSpublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublications system table
ms.assetid: 7a0b3457-7265-4f24-a255-7f055d908f20
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e5e6b1f9ab0d4cbd42e88ae4480d55625ba434e8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mspublications-transact-sql"></a>MSpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSpublications** tabella contiene una riga per ogni pubblicazione replicata da un server di pubblicazione. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**Pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**publication_id**|**int**|ID della pubblicazione.|  
|**publication_type**|**int**|Tipo di pubblicazione:<br /><br /> **0** = transazionale.<br /><br /> **1** = snapshot.<br /><br /> **2** = unione nell'indice.|  
|**thirdparty_flag**|**bit**|Indica se una pubblicazione è un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **1** = origine dei dati diverso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**independent_agent**|**bit**|Indica se per questa pubblicazione è disponibile un agente di distribuzione autonomo.|  
|**immediate_sync**|**bit**|Indica se i file di sincronizzazione vengono creati o aggiornati a ogni esecuzione dell'agente snapshot.|  
|**allow_push**|**bit**|Indica se è possibile creare sottoscrizioni di tipo push per la pubblicazione specificata.|  
|**allow_pull**|**bit**|Indica se è possibile creare sottoscrizioni di tipo pull per la pubblicazione specificata.|  
|**allow_anonymous**|**bit**|Indica se è possibile creare sottoscrizioni anonime per la pubblicazione specificata.|  
|**description**|**nvarchar(255)**|Descrizione della pubblicazione.|  
|**vendor_name**|**Nvarchar (100)**|Nome del produttore se il server di pubblicazione non è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Conservazione**|**int**|Periodo di memorizzazione della pubblicazione in ore.|  
|**sync_method**|**int**|Metodo di sincronizzazione:<br /><br /> **0** = nativa (genera l'output di copia bulk in modalità nativa di tutte le tabelle).<br /><br /> **1** = character (genera un output di copia bulk in modalità carattere di tutte le tabelle).<br /><br /> **3** = concurrent (genera output di copia bulk in modalità nativa di tutte le tabelle senza bloccare le tabelle durante lo snapshot).<br /><br /> **4** = Concurrent_c (genera un output di copia bulk in modalità carattere di tutte le tabelle senza bloccare le tabelle durante lo snapshot)<br /><br /> I valori **3** e **4** sono disponibili per la replica transazionale e di tipo merge, ma non per la replica snapshot.|  
|**allow_subscription_copy**|**bit**|Abilita o disabilita la funzione di copia dei database di sottoscrizione che sottoscrivono la pubblicazione. **0** indica che la copia è disabilitata, e **1** significa che è abilitata.|  
|**thirdparty_options**|**int**|Specifica se la visualizzazione di una pubblicazione nella cartella replica in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] viene eliminata:<br /><br /> **0** = Visualizza una pubblicazione eterogenea nella cartella replica in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].<br /><br /> **1** = disattiva la visualizzazione una pubblicazione eterogenea nella cartella replica in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|**allow_queued_tran**|**bit**|Specifica se la pubblicazione consente l'aggiornamento in coda:<br /><br /> **0 =** pubblicazione è non in coda.<br /><br /> **1** = pubblicazione è in coda.|  
|**options**|**int**|Informazioni non disponibili in questa versione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
