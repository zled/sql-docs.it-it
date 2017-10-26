---
title: "Configurare il data warehouse del punto di controllo dell'utilità (Utilità SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 05a436bf21810e3c05c2f745d6f0c067f61d0d35
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Configurazione del data warehouse del punto di controllo dell'utilità (Utilità SQL Server)
  I dati raccolti dalle istanze gestite di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono archiviati nel data warehouse di gestione dell'utilità. Il nome del file del data warehouse di gestione dell'utilità è sysutility_mdw.  
  
 È possibile configurare il periodo di memorizzazione dei dati in tale data warehouse. Per altre informazioni, vedere [Amministrazione utilità &#40;Utilità SQL Server&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d).  
  
 Le impostazioni di configurazione seguenti non sono configurabili in questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Nome del data warehouse di gestione dell'utilità: Sysutility_mdw.  
  
-   Frequenza di caricamento del set di raccolta: ogni 15 minuti.  
  
 La directory dell'utilità UMDW è configurabile: \<Unità di sistema>:\Programmi\Microsoft SQL Server\MSSQL10_50.<Nome_UCP>\MSSQL\Data\\, dove \<Unità di sistema> è in genere l'unità C:\. Il file di log, Sysutility_mdw_\<GUIDA>_LOG, si trova nella stessa directory.  
  
> [!NOTE]  
>  È possibile modificare la posizione del file data warehouse di gestione dell'utilità (UMDW) sysutility_mdw utilizzando i comandi collega/scollega o l'istruzione ALTER DATABASE. È consigliabile utilizzare l'istruzione ALTER DATABASE. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  

