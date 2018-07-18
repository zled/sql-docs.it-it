---
title: MSSQLSERVER_1457 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 85a3954b37ca6f3467bf1fc0d4fafda7dadb59ad
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver1457"></a>MSSQLSERVER_1457
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1457|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_PAGE_UNDO_PENDING|  
|Testo del messaggio|La sincronizzazione del database mirror '%.*ls' è stata interrotta, lasciando il database in uno stato inconsistente. Comando ALTER DATABASE non riuscito. Verificare che il database mirror sia nuovamente attivo e online, quindi riconnettere l'istanza del server mirror e consentire al database mirror di completare la sincronizzazione.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio indica che l'istruzione ALTER DATABASE *nome_database* SET PARTNER OFF non è stata eseguita. Il tentativo non riuscito di rimuovere il mirroring del database ha interrotto la sincronizzazione del database mirror. Il database si trova in uno stato inconsistente.  
  
## <a name="user-action"></a>Azione dell'utente  
Per risolvere il problema, è possibile eseguire una delle operazioni seguenti:  
  
-   Ripristinare il contatto tra il server mirror e il server principale per consentire la sincronizzazione del database mirror.  
  
-   Eliminare il database mirror.  
  
    Dopo aver eliminato il database mirror, sarà possibile crearne uno nuovo dai backup.  
  
    > [!NOTE]  
    > È possibile eliminare il database mirror quando il mirroring è ancora abilitato solo dopo un'istruzione SET PARTNER OFF non riuscita.  
  
## <a name="see-also"></a>Vedere anche  
[Mirroring del database &#40;SQL Server&#41;](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[Impostazione del mirroring del database &#40;SQL Server&#41;](~/database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
[Rimozione del mirroring del database &#40;SQL Server&#41;](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
[Preparazione di un database mirror per il mirroring &#40;SQL Server&#41;](~/database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
