---
title: Tabelle di cronologia di backup o ripristino grandi aggiornamento potrebbe sembrare non rispondere | Documenti Microsoft
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
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b7d3f6c5734f743d83a712cea745c3816bcdbc0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063995"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>Se sono presenti tabelle di cronologia di backup o ripristino di grandi dimensioni, l'aggiornamento potrebbe sembrare che non risponde
  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sono state aggiunte nuove colonne ad alcune delle tabelle di cronologia di backup e ripristino. Per aggiornare queste tabelle, è necessario modificarle in modo da aggiungere le nuove colonne. Se una o più di queste tabelle contengono un numero elevato di righe, l'aggiornamento richiederà molto tempo per l'istruzione ALTER TABLE che aggiunge colonne a tale tabella.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 L'aggiornamento potrebbe apparire bloccato se una delle seguenti tabelle di cronologia di backup o ripristino contiene un numero elevato di righe:  
  
-   **backupfile**  
  
-   **backupmediafamily**  
  
-   **backupmediaset**  
  
-   **backupset**  
  
-   **restorefile**  
  
-   **restorefilegroup**  
  
-   **restorehistory**  
  
 Se una di queste tabelle contiene almeno 10.000 righe, verrà segnalato un errore di non conformità. La tabella che supera il numero consentito di righe non viene indicata. La prima tabella che supera le 10.000 righe genera l'errore.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di aggiornare un database, se una di queste tabelle supera le 10.000 righe, si consiglia di ridurre questo numero. Per ridurre le righe in tutte queste tabelle, è possibile eseguire la **sp_delete_backuphistory** stored procedure. Questa procedura elimina le voci in tutte le tabelle di cronologia di backup e ripristino relative a set di backup precedenti a una data specificata. Per altre informazioni, vedere [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
> [!NOTE]  
>  È possibile aggiornare un database le cui tabelle di cronologia di backup e ripristino contengono più di 10.000 righe, ma il processo potrebbe sembrare bloccato durante la modifica di tabelle di grandi dimensioni. Le dimensioni delle tabelle influiscono sul tempo richiesto per completare il programma di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
