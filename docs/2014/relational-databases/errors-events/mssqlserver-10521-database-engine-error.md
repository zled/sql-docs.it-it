---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18d823ff21a38c3eeee8df725c9a38172080d40e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421080"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10521|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_PARAM_NEEDED|  
|Testo del messaggio|Impossibile creare la Guida di piano ' %. \*ls' perché `@type` è stato specificato come '%ls' e il parametro '%ls' è NULL. Questo tipo richiede un valore non NULL per il parametro. Specificare un valore non NULL per il parametro oppure impostare un tipo che consenta un valore NULL per il parametro.|  
  
## <a name="explanation"></a>Spiegazione  
 Il tipo indicato in `@type` richiede un valore non Null per il parametro specificato, ma è stato fornito un valore Null.  
  
## <a name="user-action"></a>Azione dell'utente  
 Specificare un valore non NULL per il parametro oppure impostare un tipo che consenta un valore NULL per il parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Guide di piano](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
