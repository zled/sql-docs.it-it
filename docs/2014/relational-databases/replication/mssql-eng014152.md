---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b115ac5bcaee609dd56f3437141171f3b422a638
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064223"
---
# <a name="mssqleng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14152|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Replica-%s: ripetizione dell'esecuzione dell'agente %s pianificata. %s|  
  
## <a name="explanation"></a>Spiegazione  
 L'agente di replica specificato è stato pianificato in modo da tentare nuovamente l'esecuzione dell'operazione richiesta. Verranno eseguiti nuovi tentativi finché non verrà raggiunto il numero massimo di tentativi configurato per il passaggio del processo.  
  
 Viene in genere eseguito un nuovo tentativo per i motivi seguenti:  
  
-   È stato superato il valore di **QueryTimeout** .  
  
-   È stato superato il valore di **LoginTimeout** .  
  
-   Il processo di replica è stato scelto come vittima del deadlock.  
  
## <a name="user-action"></a>Azione dell'utente  
 Se il messaggio relativo a nuovi tentativi non viene visualizzato di frequente, non è richiesto nessun intervento da parte dell'utente.  
  
 Utilizzare [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) per visualizzare l'impostazione corrente relativa al numero massimo di tentativi di esecuzione del passaggio **Run agent** per l'agente di replica specificato. È possibile utilizzare il parametro **@retry_attempts** della stored procedure [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) per modificare il numero di tentativi di esecuzione di un passaggio del processo.  
  
 Se il messaggio relativo a nuovi tentativi viene visualizzato di frequente, risolvere il problema in base al messaggio che causa l'esecuzione di nuovi tentativi. Verificare nella cronologia dell'agente la presenza di messaggi che indicano il motivo per cui è stato necessario pianificare il nuovo tentativo. In alcuni casi potrebbe essere necessario attivare un livello di registrazione più dettagliato per l'agente di replica. Per ulteriori informazioni sulla configurazione della registrazione per la replica, vedere l'articolo [312292](http://support.microsoft.com/kb/312292)della Microsoft Knowledge Base.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)  
  
  
