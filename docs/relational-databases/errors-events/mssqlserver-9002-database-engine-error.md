---
title: MSSQLSERVER_9002 | Microsoft Docs
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
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fafb1765edbf93a9c356bda314207c70cb6ffb24
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9002|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LOG_IS_FULL|  
|Testo del messaggio|Il log delle transazioni per il database '%.*ls' è pieno. Per sapere perché non è possibile riutilizzare lo spazio nel log, vedere la colonna log_reuse_wait_desc in sys.databases.|  
  
## <a name="explanation"></a>Spiegazione  
Lo spazio nel log del database è esaurito. Nella colonna **log_reuse_wait_desc** in **sys.databases** viene descritto il motivo per cui non è possibile usare di nuovo lo spazio nel log.  
  
## <a name="user-action"></a>Azione dell'utente  
Usare **sys.databases** per determinare perché il log è pieno e quindi correggere tale condizione. Per ulteriori informazioni, vedere l'articolo sulla risoluzione dei problemi relativi a un log delle transazioni pieno (Errore 9002) nella documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
[Risolvere i problemi relativi a un log delle transazioni completo &#40;errore di SQL Server 9002&#41;](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
