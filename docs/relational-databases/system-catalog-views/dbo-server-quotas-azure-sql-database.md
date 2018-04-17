---
title: dbo. server_quotas (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 08/02/2016
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 66f6e2c1cae1b8743314a8a9ff844040e1f91f35
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **IMPORTANTE** Ciò si applica a  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 solo!**  
>   
>  Questa funzionalità si trova nello stato anteprima. Non specificare una dipendenza dall'implementazione specifica di questa funzionalità perché potrebbe essere modificata o rimossa in una versione successiva.  
  
 Restituisce i tipi di quote di database disponibili nel server.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|Tipo di quota per il server. Il tipo **Premium_database** è equivalente ai database con una prenotazione di risorse.|  
|quota_value|**int**|Numero di tipo di quota consentito nel server.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di database Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
