---
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e6f054d87e119a64c04bf0770182672a7a17e5d6
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng014144"></a>MSSQL_ENG014144
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14144|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Al Sottoscrittore '%s' sono associate sottoscrizioni nel database di pubblicazione '%s'. Impossibile eliminarlo.|  
  
## <a name="explanation"></a>Spiegazione  
 Non è possibile rimuovere dal ruolo del Sottoscrittore un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è configurata come Sottoscrittore fino a che vi sono sottoscrizioni attive configurate per quell'istanza.  
  
## <a name="user-action"></a>Azione dell'utente  
 Eliminare tutte le sottoscrizioni associate prima di tentare di modificare lo stato del Sottoscrittore dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Per trovare le sottoscrizioni, eseguire [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) nel database di pubblicazione sul server di pubblicazione.  
  
2.  Per eliminare le sottoscrizioni, eseguire [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md) nel database di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
