---
title: sysdac_instances_internal (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5389e86dee17cd4a8a4e5432e98d7c5a554c1469
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-tier-application-tables---sysdacinstancesinternal"></a>Tabelle di applicazione livello dati - sysdac_instances_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare una riga per ogni istanza di applicazione livello dati distribuita in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Questa tabella è archiviata nello schema dbo nel database msdb.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|Identificatore dell'istanza di applicazione livello dati.|  
|nome_istanza|**sysname**|Nome dell'istanza di applicazione livello dati specificato alla distribuzione dell'istanza.|  
|type_name|**sysname**|Nome dell'applicazione livello dati specificata alla creazione del pacchetto di applicazione livello dati.|  
|type_version|**nvarchar(64)**|Versione dell'applicazione livello dati specificata alla creazione del pacchetto di applicazione livello dati.|  
|description|**nvarchar(4000)**|Descrizione dell'applicazione livello dati scritta alla creazione del pacchetto di applicazione livello dati.|  
|type_stream|**varbinary(max)**|Flusso di bit contenente la rappresentazione codificata degli oggetti logici, ad esempio tabelle e viste, contenuti nell'applicazione livello dati.|  
|date_created|**datetime**|Data e ora di creazione dell'istanza di applicazione livello dati.|  
|created_by|**sysname**|Account di accesso utilizzato per la creazione dell'istanza di applicazione livello dati.|  
  
## <a name="remarks"></a>Osservazioni  
 Accesso in sola lettura a questa vista è disponibile per tutti gli utenti con autorizzazioni per connettersi al database master.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server sysadmin.  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni livello dati](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
