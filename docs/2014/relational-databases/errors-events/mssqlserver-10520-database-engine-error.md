---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 79274cf031103e50151b6e93a9daff781005abad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084851"
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10520|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_PARAM_NOT_ALLOWED|  
|Testo del messaggio|Impossibile creare la guida di piano '%.*ls' perché @type è stato specificato come '%ls' ed è stato specificato un valore non NULL per il parametro '%ls'. Questo tipo richiede un valore NULL per il parametro. Specificare NULL per il parametro oppure impostare un tipo che consenta un valore non NULL per il parametro.|  
  
## <a name="explanation"></a>Spiegazione  
 Il tipo indicato in @type richiede un valore NULL per il parametro specificato, ma è stato fornito un valore non NULL.  
  
## <a name="user-action"></a>Azione dell'utente  
 Specificare NULL per il parametro oppure impostare un tipo che consenta un valore non NULL per il parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Guide di piano](../performance/plan-guides.md)  
  
  
