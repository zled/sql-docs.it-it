---
title: MSSQLSERVER_10537 | Microsoft Docs
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
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3329a982d09e38614d6297d1776f7f58e5586f5b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10537"></a>MSSQLSERVER_10537
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10537|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_DUP_ENABLED|  
|Testo del messaggio|Impossibile abilitare la guida di pano '%.*ls' perché la guida di piano '%.\*ls' abilitata contiene lo stesso ambito e lo stesso valore di offset iniziale dell'istruzione. Disabilitare la guida di piano esistente prima di abilitare la guida di piano specificata.|  
  
## <a name="explanation"></a>Spiegazione  
Una guida di piano esistente abilitata contiene lo stesso ambito e lo stesso valore di offset iniziale dell'istruzione presente nella guida di piano specificata.  
  
## <a name="user-action"></a>Azione dell'utente  
Disabilitare la guida di piano esistente prima di abilitare la guida di piano specificata.  
  
## <a name="see-also"></a>Vedere anche  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
