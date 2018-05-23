---
title: Finestra Thread | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 99fad1df0f1eab5ee6bd01f816ca9007c7d66f64
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="transact-sql-debugger---threads-window"></a>Debugger Transact-SQL - Finestra Thread
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Nella finestra **Thread** vengono visualizzate informazioni sul thread del [!INCLUDE[ssDE](../../includes/ssde-md.md)] usato dalla sessione dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] di cui viene eseguito il debug. Per visualizzare le informazioni sul thread, è necessario utilizzare la modalità di debug.  
  
## <a name="task-list"></a>Elenco attività  
 **Per accedere alla finestra Thread**  
  
-   Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Thread**.  
  
## <a name="columns"></a>Colonne  
 **ID**  
 Numero di identificazione univoco assegnato al thread dal debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] . È possibile ottenere ulteriori informazioni sul thread selezionando una riga nella vista a gestione dinamica sys.dm_os_threads.  
  
 Se non è attiva la modalità lightweight pooling, selezionare la riga in cui il valore di os_thread_id corrisponde al valore specificato nella colonna **ID** . Se è attiva la modalità lightweight pooling, selezionare la riga in cui il valore di fiber_context_address corrisponde al valore specificato nella colonna **ID** .  
  
 **Nome**  
 Consente di visualizzare informazioni sulla sessione del [!INCLUDE[ssDE](../../includes/ssde-md.md)] in formato **NomeComputer/NomeIstanza [SPID]**.  
  
 **NomeComputer**  
 Nome del computer che esegue l'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a cui è connessa la sessione dell'editor di query.  
  
 **InstanceName**  
 Nome dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a cui è connessa la sessione dell'editor di query.  
  
 **[SPID]**  
 ID di processo della sessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che identifica in modo univoco la sessione. È possibile ottenere ulteriori informazioni sulla sessione selezionando la riga nella vista sys.sysprocesses che include lo stesso valore nella colonna spid.  
  
 **Percorso**  
 Consente di visualizzare il nome del file script utilizzato nella sessione dell'editor di query di cui viene eseguito il debug.  
  
 **Priorità**  
 Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] non supporta questa caratteristica.  
  
 **Sospendi**  
 Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] non supporta questa caratteristica.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)  
  
  
