---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 470dc989a6f3bbe7009069eeeb2b99aec96cce92
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429500"
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
    
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
 [Risolvere i problemi relativi a un log delle transazioni completo &#40;Errore di SQL Server 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
