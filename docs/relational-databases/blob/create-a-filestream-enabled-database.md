---
title: Creare un database abilitato per FILESTREAM | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: blob
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 23d5b47658172921c66ee02de3d42edee1bdf2fb
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="create-a-filestream-enabled-database"></a>Creazione di un database abilitato per FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questo argomento viene illustrato come creare un database che supporti FILESTREAM. Poiché in FILESTREAM viene utilizzato un tipo speciale di filegroup, quando si crea il database è necessario specificare la clausola CONTAINS FILESTREAM per almeno un filegroup.  
  
 Un filegroup FILESTREAM può contenere più di un file. Per un esempio di codice che illustra come creare un filegroup FILESTREAM contenente più file, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
### <a name="to-create-a-filestream-enabled-database"></a>Per creare un database abilitato per FILESTREAM  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic su **Nuova query** per visualizzare l'editor di query.  
  
2.  Copiare il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] dall'esempio seguente e incollarlo nell'Editor di query. Tramite il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] viene creato un database abilitato per FILESTREAM denominato Archive.  
  
    > [!NOTE]  
    >  Per eseguire questo script, è necessario che la directory C:\Data esista.  
  
3.  Per compilare il database, fare clic su **Esegui**.  
  
## <a name="example"></a>Esempio  
 Nel codice di esempio seguente viene creato un database denominato `Archive`. Il database contiene tre filegroup: `PRIMARY`, `Arch1`e `FileStreamGroup1`. `PRIMARY` e `Arch1` sono filegroup normali che non possono contenere dati FILESTREAM. `FileStreamGroup1` è il filegroup `FILESTREAM` .  
  
 [!code-sql[FILESTREAM#FS_CreateDB](../../relational-databases/blob/codesnippet/tsql/create-a-filestream-enab_1.sql)]  
  
 Per un filegroup `FILESTREAM` , `FILENAME` fa riferimento a un percorso. È necessario che il percorso fino all'ultima cartella esista già, mentre l'ultima cartella non deve essere presente. In questo esempio è necessario che `c:\data` esista. La sottocartella `filestream1` tuttavia non può esistere quando si esegue l'istruzione `CREATE DATABASE` . Per altre informazioni sulla sintassi, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 Dopo avere eseguito l'esempio precedente, nella cartella c:\Data\filestream1 sono presenti il file filestream.hdr e la cartella $FSLOG. Il file filestream.hdr è un file di intestazione per il contenitore FILESTREAM.  
  
> [!IMPORTANT]  
>  Il file filestream.hdr è un importante file di sistema. Tale file contiene informazioni di intestazione di FILESTREAM. Non rimuoverlo o modificarlo.  
  
 Per database esistenti, è possibile utilizzare l'istruzione [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) per aggiungere un filegroup FILESTREAM.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
