---
title: sp_dbmmonitoraddmonitoring (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aa3215b176fe96b0e449f95b01afa79f20d6371
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spdbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un processo di Monitoraggio mirroring del database che aggiorna periodicamente lo stato di mirroring per ogni database con mirroring nell'istanza del server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *update_period*  
 Specifica l'intervallo, in minuti, tra gli aggiornamenti. Il valore è compreso tra 1 e 120 minuti. Il valore predefinito è 1 minuto.  
  
> [!NOTE]  
>  Se il periodo di aggiornamento è impostato su un valore troppo basso, i tempi di risposta per i client potrebbero aumentare.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Per eseguire questa procedura è necessario che sia consentita l'esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nell'istanza del server e per eseguire il processo di Monitoraggio mirroring del database è necessario che SQL Server Agent sia in esecuzione.  
  
 Se il mirroring del database viene avviato da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **sp_dbmmonitoraddmonitoring** viene eseguita automaticamente. Se si avvia mirroring manualmente tramite le istruzioni ALTER DATABASE, per monitorare un database con mirroring nell'istanza del server, è necessario eseguire **sp_dbmmonitoraddmonitoring** manualmente.  
  
> [!NOTE]  
>  Se si esegue **sp_dbmmonitoraddmonitoring** prima di configurare il mirroring del database, il processo di monitoraggio verranno eseguiti, ma non verrà aggiornata la tabella dello stato in quale database è archiviata la cronologia di monitoraggio mirroring del.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene avviato il monitoraggio con un periodo di aggiornamento di `3` minuti.  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
