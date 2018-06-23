---
title: Eseguire il backup in un set di supporti con mirroring (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ee57f4caeba9747e3d4d9b1ac8577d7bf0ca486
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168326"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Backup in un set di supporti con mirroring (Transact-SQL)
  Questo argomento descrive come usare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) per specificare un set di supporti con mirroring durante l'esecuzione del backup di un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Nell'istruzione BACKUP specificare il primo mirror nella clausola TO, quindi specificare ogni mirror nella relativa clausola MIRROR TO. È necessario che le clausole TO e MIRROR TO specifichino lo stesso numero e tipo di dispositivo di backup.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato il set di supporti con mirroring indicato nella figura precedente e viene eseguito il backup del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] su entrambi i mirror.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 **Per eseguire il ripristino da un backup con mirroring**  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Set di supporti di backup con mirroring &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  
