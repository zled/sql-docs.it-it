---
title: 'Lezione 3: Scrivere un Backup completo del Database al servizio di archiviazione Blob di Azure di Windows | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 4a28465f0175be0bfc12e5c9d51a267ae6597ec6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236081"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Lezione 3: Scrivere un backup completo del database nel servizio di archiviazione BLOB di Windows Azure
  In questa lezione viene illustrato l'utilizzo dell'istruzione tsql per eseguire un backup completo del database nel servizio di archiviazione BLOB di Windows Azure.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Eseguire un backup completo del database nel servizio di archiviazione BLOB di Windows Azure  
 Per creare un backup completo del database, attenersi ai passaggi seguenti:  
  
1.  Connettersi a [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Nel **Esplora oggetti**, connettersi all'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  Sulla barra del menu Standard fare clic su **Nuova query**.  
  
4.  Copiare e incollare l'esempio seguente nella finestra Query, modificare se necessario, quindi fare clic su **Esegui**.  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  In Esplora oggetti connettersi alla risorsa di archiviazione Azure. Sfogliare per individuare il contenitore e i file di backup appena creati.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 4: Eseguire un ripristino da un Backup completo del Database](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  
