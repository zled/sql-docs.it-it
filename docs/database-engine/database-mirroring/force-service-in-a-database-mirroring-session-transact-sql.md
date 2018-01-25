---
title: Uso forzato del servizio in una sessione di mirroring del database (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-mirroring
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
caps.latest.revision: "40"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d2293e47ca9ec237bc910815f79a11ebc679ef3
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a>Utilizzo forzato del servizio in una sessione di mirroring del database (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Nella modalità a prestazioni elevate e in quella a sicurezza elevata senza failover automatico, se si verifica un errore nel server principale mentre è disponibile il server mirror, il proprietario del database può rendere disponibile il database forzando il failover del servizio nel database mirror, sebbene tale operazione implichi la possibile perdita di dati. Questa opzione è disponibile esclusivamente nelle condizioni seguenti:  
  
-   Il server principale non è disponibile.  
  
-   WITNESS è impostato su OFF o connesso al server mirror.  
  
> [!CAUTION]  
>  Il servizio forzato rappresenta esclusivamente un metodo di ripristino di emergenza. L'utilizzo forzato del servizio può implicare perdite di dati. È quindi consigliabile forzare il servizio solo se si è consapevoli che il ripristino immediato del servizio nel database può causare perdite di dati. Se l'utilizzo forzato del servizio implica il rischio della perdita di dati importanti, è consigliabile arrestare il mirroring e risincronizzare manualmente i database. Per altre informazioni sui rischi dell'uso forzato del servizio, vedere [Modalità di funzionamento del mirroring del database](../../database-engine/database-mirroring/database-mirroring-operating-modes.md).  
  
 L'utilizzo forzato del servizio comporta l'interruzione della sessione e l'avvio di un nuovo fork di recupero. L'effetto dell'utilizzo forzato del servizio è simile alla rimozione del mirroring e al recupero del database principale precedente. Tuttavia, l'utilizzo forzato del servizio facilita la risincronizzazione dei database, con possibile perdita di dati, quando viene ripreso il mirroring.  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a>Per forzare il servizio in una sessione di mirroring del database  
  
1.  Connettersi al server mirror.  
  
2.  Eseguire l'istruzione seguente:  
  
     ALTER DATABASE *<nome_database>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS  
  
     dove *<nome_database>* corrisponde al database con mirroring.  
  
     Il server mirror esegue immediatamente la transizione al server principale e il mirroring viene sospeso.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
