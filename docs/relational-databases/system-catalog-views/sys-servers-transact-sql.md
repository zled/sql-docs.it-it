---
title: sys.servers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- servers_TSQL
- sys.servers_TSQL
- servers
- sys.servers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.servers catalog view
ms.assetid: 4e774ed9-4e83-4726-9f1d-8efde8f9feff
caps.latest.revision: 53
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: e8c70890bf8571621cd82aaab7e3d2796eb3bb0e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43038814"
---
# <a name="sysservers-transact-sql"></a>sys.servers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Contiene una riga per ogni server collegato o remoto registrato e una riga per il server locale che dispone **server_id** = 0.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID locale del server collegato.|  
|**name**|**sysname**|Quando **server_id** = 0, questo è il nome del server.<br /><br /> Quando **server_id** > 0, si tratta del nome locale del server collegato.|  
|**product**|**sysname**|Nome del prodotto del server collegato. "SQL Server" indica che si tratta di un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**provider**|**sysname**|Nome del provider OLE DB per la connessione al server collegato.|  
|**data_source**|**nvarchar(4000)**|Proprietà di connessione dell'origine dei dati OLE DB.|  
|**Posizione**|**nvarchar(4000)**|Proprietà di connessione della posizione OLE DB. Restituisce NULL se la colonna non include alcun valore.|  
|**provider_string**|**nvarchar(4000)**|Proprietà di connessione della stringa del provider OLE DB.<br /><br /> È NULL tranne nei casi in cui il chiamante dispone dell'autorizzazione ALTER ANY LINKED SERVER.|  
|**catalog**|**sysname**|Proprietà di connessione del catalogo OLE DB. Restituisce NULL se la colonna non include alcun valore.|  
|**connect_timeout**|**int**|Timeout della connessione espresso in secondi. Restituisce 0 se non si specifica alcun valore.|  
|**query_timeout**|**int**|Timeout della query espresso in secondi. Restituisce 0 se non si specifica alcun valore.|  
|**is_linked**|**bit**|0 = è un server di tipo obsoleto aggiunto tramite **sp_addserver**, con diversi RPC e transazioni distribuite.<br /><br /> 1 = Server collegato standard.|  
|**is_remote_login_enabled**|**bit**|L'opzione RPC è impostata per consentire gli accessi remoti in entrata per questo server.|  
|**is_rpc_out_enabled**|**bit**|Sono abilitate le chiamate RPC in uscita (da questo server).|  
|**is_data_access_enabled**|**bit**|Il server è abilitato per le query distribuite.|  
|**is_collation_compatible**|**bit**|Le regole di confronto dei dati remoti vengono considerate compatibili con i dati locali se non sono disponibili informazioni sulle regole di confronto.|  
|**uses_remote_collation**|**bit**|Il valore 1 indica che vengono utilizzate le regole di confronto segnalate dal server remoto. In caso contrario, vengono utilizzate le regole di confronto specificate dalla colonna successiva.|  
|**nome_regole_di_confronto**|**sysname**|Nome delle regole di confronto da utilizzare oppure NULL se vengono utilizzate le regole di confronto locali.|  
|**lazy_schema_validation**|**bit**|Il valore 1 indica che la convalida dello schema non viene verificata all'avvio della query.|  
|**is_system**|**bit**|È possibile accedere a questo server solo dal sistema interno.|  
|**is_publisher**|**bit**|Il server è un server di pubblicazione per la replica.|  
|**is_subscriber**|**bit**|Il server è un Sottoscrittore per la replica.|  
|**is_distributor**|**bit**|Il server è un server di distribuzione per la replica.|  
|**is_nonsql_subscriber**|**bit**|Il server è un Sottoscrittore non SQL Server per la replica.|  
|**is_remote_proc_transaction_promotion_enabled**|**bit**|Se 1, la chiamata di una stored procedure remota comporta l'avvio di una transazione distribuita e l'integrazione della transazione in MS DTC. Per altre informazioni, vedere [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md).|  
|**modify_date**|**datetime**|Data dell'ultima modifica delle informazioni relative al server.|  
  
## <a name="permissions"></a>Permissions  
 Il valore in **provider_string** è sempre NULL a meno che il chiamante dispone dell'autorizzazione ALTER ANY LINKED SERVER.  
  
 Non sono necessarie autorizzazioni per visualizzare il server locale (**server_id** = 0).  
  
 Quando si crea un server collegato o remoto, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea un mapping di account di accesso predefinito per il **pubblico** ruolo del server. Di conseguenza, per impostazione predefinita tutti gli account di accesso possono visualizzare tutti i server collegati e remoti. Per limitare la visibilità per questi server, rimuovere il mapping di account di accesso predefinito eseguendo [sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) e specificando NULL per il *locallogin* parametro.  
  
 Se il mapping predefinito degli account di accesso viene eliminato, solo gli utenti aggiunti esplicitamente come account di accesso collegato o remoto possono visualizzare i server collegati o remoti per cui dispongono di un account di accesso. Per visualizzare tutti i server collegati e remoti in seguito all'eliminazione del mapping predefinito degli account di accesso, sono richieste le autorizzazioni seguenti:  
  
-   ALTER ANY LINKED SERVER o ALTER ANY LOGIN ON SERVER  
  
-   Appartenenza al gruppo il **setupadmin** oppure **sysadmin** ruoli predefiniti del server  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo di server collegati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
  
