---
title: sysmail_event_log (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_event_log
- sysmail_event_log_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_event_log database mail view
ms.assetid: 440bc409-1188-4175-afc4-c68e31e44fed
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2f9818bda47d9e0ffac256220f36efa1c5c6360
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysmaileventlog-transact-sql"></a>sysmail_event_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni messaggio di Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito dal sistema di Posta elettronica database. Il termine messaggio in questo contesto indica un messaggio ad esempio di errore, non un messaggio di posta elettronica. Configura il **livello di registrazione** parametro utilizzando il **configurazione parametri di sistema** la finestra di dialogo di configurazione guidata posta elettronica Database o [sysmail_configure_sp](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md)stored procedure per determinare i messaggi restituiti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Log_id**|**int**|Identificatore degli elementi nel log.|  
|**event_type**|**varchar (11)**|Tipo di avviso inserito nel log. I possibili valori sono errori, avvisi, messaggi informativi, messaggi di operazione riuscita e altri messaggi interni.|  
|**log_date**|**datetime**|Data e ora di creazione della voce del log.|  
|**description**|**nvarchar(max)**|Testo del messaggio registrato.|  
|**process_id**|**int**|ID di processo del programma esterno Posta elettronica database. In genere, viene modificato a ogni avvio del programma esterno Posta elettronica database.|  
|**mailitem_id**|**int**|Identificatore dell'elemento di posta nella coda della posta. Se il messaggio non è correlato a un elemento di posta elettronica specifico, viene restituito NULL.|  
|**account_id**|**int**|Il **account_id** dell'account correlato all'evento. Se il messaggio non è correlato a un account specifico, viene restituito NULL.|  
|**last_mod_date**|**datetime**|Data e ora dell'ultima modifica della riga.|  
|**last_mod_user**|**sysname**|Autore dell'ultima modifica della riga. Per i messaggi di posta elettronica corrisponde all'utente che ha inviato il messaggio. Per i messaggi generati dal programma esterno Posta elettronica database corrisponde al contesto utente del programma.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando la risoluzione dei problemi di posta elettronica Database, eseguire la ricerca di **sysmail_event_log** visualizzazione per gli eventi correlati a errori di posta elettronica. Alcuni messaggi, ad esempio quelli relativi agli errori del programma esterno Posta elettronica database, non sono associati a messaggi di posta elettronica specifici. Per cercare gli errori correlati a messaggi di posta elettronica specifici, cercare il **mailitem_id** della posta elettronica non riuscita nel **sysmail_faileditems** consente di visualizzare e quindi cercare la **sysmail_event_log**per i messaggi correlati a tale **mailitem_id**. Quando viene restituito un errore da **sp_send_dbmail**, messaggio di posta elettronica non viene inviato al sistema di posta elettronica Database e l'errore non viene visualizzato in questa vista.  
  
 Quando i tentativi di recapito con singoli account hanno esito negativo, i messaggi di errore rimangono visualizzati durante i successivi tentativi di invio fino a quando il recapito dell'elemento di posta non ha definitivamente esito positivo o negativo. In caso di esito positivo finale, tutti gli errori accumulati vengono registrati come avvisi separati tra cui la **account_id**. Pertanto, è possibile che vengano visualizzati messaggi di avviso anche se il messaggio di posta elettronica è stato inviato. In caso di errore di recapito finale, tutti gli avvisi precedenti vengono registrati come messaggio di errore senza un **account_id**, dal momento che tutti gli account non sono riuscita.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessario essere un membro del **sysadmin** ruolo predefinito del server o **DatabaseMailUserRole** ruolo del database per accedere a questa vista. I membri di **DatabaseMailUserRole** che non sono membri del **sysadmin** ruolo, è possibile visualizzare solo gli eventi per i messaggi di posta elettronica che hanno inviato personalmente.  
  
## <a name="see-also"></a>Vedere anche  
 [sysmail_faileditems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [Programma esterno di Posta elettronica database](../../relational-databases/database-mail/database-mail-external-program.md)  
  
  
