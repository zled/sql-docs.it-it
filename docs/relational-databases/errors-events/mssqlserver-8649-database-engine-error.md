---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61aa34e8e5b47b50791c8d325afff7698ddd0047
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8649|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|COST_TOO_HIGH|  
|Testo del messaggio|La query è stata annullata perché il suo costo stimato (%d) è maggiore della soglia configurata, pari a %d. Contattare l'amministratore del sistema.|  
  
## <a name="explanation"></a>Spiegazione  
La query è stata annullata perché il suo costo stimato supera la soglia configurata impostata per QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare l'opzione QUERY_GOVERNOR_COST_LIMIT su un valore più elevato.  
  
## <a name="see-also"></a>Vedere anche  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
