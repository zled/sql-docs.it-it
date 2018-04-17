---
title: Sys. sysoledbusers (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
caps.latest.revision: 34
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d413a9a07af247a62611946bf687c53e6f42d878
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Questa tabella di sistema di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] è disponibile come vista in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per motivi di compatibilità con le versioni precedenti. È consigliabile utilizzare [viste del catalogo](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) invece.  
  
 È contenuta una riga per il mapping di ogni utente e password per il server collegato specificato. **sysoledbusers** viene archiviato nel **master** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|ID di sicurezza (SID) del server.|  
|**rmtloginame**|**nvarchar (**128**)**|Nome dell'account di accesso remoto che **loginsid** esegue il mapping a per collegato **rmtservid**.|  
|**rmtpassword**|**nvarchar (**128**)**|Restituisce NULL.|  
|**loginsid**|**varbinary(**85**)**|SID dell'account di accesso locale su cui eseguire il mapping.|  
|**status**|**smallint**|Se uguale a 1, per il mapping è necessario utilizzare le credenziali dell'utente.|  
|**ChangeDate**|**datetime**|Data dell'ultima modifica delle informazioni sul mapping.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
