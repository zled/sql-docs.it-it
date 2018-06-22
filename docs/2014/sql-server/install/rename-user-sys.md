---
title: Rinominare l'utente sys | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 959eb9877fa4b73ff9bd307019976a05514b8f8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063527"
---
# <a name="rename-user-sys"></a>Rinominare l'utente sys
  Upgrade Advisor ha rilevato il nome utente **sys** in un database. Questo nome è riservato. Rinominare l'utente prima di eseguire l'aggiornamento. Se l'utente non viene rinominato, il database si troverà in stato sospetto dopo il processo di aggiornamento e non sarà disponibile finché non viene portato online.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Utente **sys** è riservato.  
  
## <a name="corrective-action"></a>Azione correttiva  
  
### <a name="before-upgrade-procedure"></a>Procedura precedente all'aggiornamento  
 Prima di aggiornare, in ogni database che contiene l'utente **sys**, eseguire le operazioni seguenti:  
  
1.  Creare un nuovo utente.  
  
2.  Utilizzare le istruzioni seguenti per visualizzare tutte le autorizzazioni concesse dall'utente **sys** e concesse all'utente **sys**.  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  Per trasferire la proprietà di tutti gli oggetti di proprietà **sys** al nuovo utente, utilizzare **sp_changeobjectowner**.  
  
4.  Eliminare l'utente **sys**.  
  
5.  Per ripristinare le autorizzazioni originali acquisite nel passaggio 2, utilizzare la clausola AS *new_user* clausola dell'istruzione GRANT.  
  
6.  Modificare gli script in modo che facciano riferimento al nuovo utente. Ad esempio, gli script che contengono istruzioni come `SELECT * FROM sys.my`_`table` devono essere modificati in `SELECT * FROM new_user.my_table`.  
  
### <a name="after-upgrade-procedure"></a>Procedura successiva all'aggiornamento  
 Se l'utente **sys** è stato rinominato non prima dell'aggiornamento, eseguire le operazioni seguenti:  
  
1.  Eseguire l'istruzione `ALTER DATABASE db_name SET ONLINE`. Il database sarà in modalità SINGLE_USER.  
  
2.  Seguire tutti i passaggi riportati nella sezione "Procedura precedente all'aggiornamento".  
  
3.  Eseguire l'istruzione `ALTER DATABASE db_name SET MULTI_USER`.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
