---
title: MSSQLSERVER_3176 | Microsoft Docs
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
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4d9c0da49aaf3f2cb8d55bf63923d6f718ff26f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157995"
---
# <a name="mssqlserver3176"></a>MSSQLSERVER_3176
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|3176|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LDDB_FILE_CLAIM|  
|Testo del messaggio|Il file '%ls' è richiesto da '%ls'(%d) e '%ls'(%d). Per rilocare uno o più file è possibile utilizzare la clausola WITH MOVE.|  
  
## <a name="explanation"></a>Spiegazione  
 Viene tentato l'utilizzo di un file per più scopi.  
  
### <a name="possible-causes"></a>Possibili cause  
 Il nome file viene già utilizzato da un altro database.  
  
## <a name="user-action"></a>Azione dell'utente  
 Ripristinare i file di database in un altro percorso. In un'istruzione RESTORE, utilizzare una clausola WITH MOVE per spostare ogni file. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] modificare i percorsi dei file nella griglia **Ripristina file di database come** nella pagina Opzioni della finestra di dialogo **Ripristina database**.  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristinare un database in una nuova posizione &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Ripristinare i file in una nuova posizione &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
