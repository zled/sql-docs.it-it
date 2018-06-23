---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c6716439038f61003abd807cefbf123ec3682b17
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158918"
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8689|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|USEPLAN_ERR_NO_DB|  
|Testo del messaggio|Il database '%.*ls' specificato nell'hint USE PLAN non esiste. Specificare un database esistente.|  
  
## <a name="explanation"></a>Spiegazione  
 Un database specificato nell'hint USE PLAN non esiste.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare che tutti i database specificati nell'hint USE PLAN esistano.  
  
## <a name="see-also"></a>Vedere anche  
 [Hint di query &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [Guide di piano](../performance/plan-guides.md)  
  
  
