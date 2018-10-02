---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 87eceb40b32841f7189b84a19752ee19fb7cb398
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743899"
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
[Hint di query &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
  
