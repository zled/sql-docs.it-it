---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c93dfdc81a37d06e6da2d1f1d2329ac378893090
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10538"></a>MSSQLSERVER_10538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10538|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_INVALID_PLANGUIDE_HANDLE|  
|Testo del messaggio|Impossibile trovare la guida di piano. L'ID della guida di piano specificato è NULL o non valido oppure l'utente non dispone dell'autorizzazione per l'oggetto a cui fa riferimento la guida di piano. Verificare che l'ID della guida di piano sia valido, che la sessione corrente sia impostata sul contesto di database corretto e di disporre dell'autorizzazione ALTER per l'oggetto a cui fa riferimento la guida di piano o dell'autorizzazione ALTER DATABASE.|  
  
## <a name="explanation"></a>Spiegazione  
L'ID della guida di piano specificato è NULL o non valido oppure l'utente non dispone dell'autorizzazione per l'oggetto a cui fa riferimento la guida di piano.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che l'ID della guida di piano sia valido, che la sessione corrente sia impostata sul contesto di database corretto e di disporre dell'autorizzazione ALTER per l'oggetto a cui fa riferimento la guida di piano o dell'autorizzazione ALTER DATABASE.  
  
## <a name="see-also"></a>Vedere anche  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
