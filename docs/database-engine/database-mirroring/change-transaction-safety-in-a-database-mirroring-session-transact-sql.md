---
title: Modifica della protezione delle transazioni in una sessione di mirroring del database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ebfbdfc875da93bbf09b683721cc6afea168771e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a>Modifica della protezione delle transazioni in una sessione di mirroring del database (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La protezione delle transazioni è l'attributo che controlla la modalità operativa della sessione. Il proprietario del database può tuttavia modificare in qualsiasi momento tale protezione. Per impostazione predefinita, il livello di protezione delle transazioni è impostato su FULL (modalità operativa sincrona).  
  
 Se la protezione delle transazioni viene disabilitata, la sessione passa alla modalità operativa asincrona che consente di ottimizzare le prestazioni. In caso di indisponibilità del server principale, il server mirror viene arrestato ma risulta disponibile come server di standby a caldo (warm standby). Per il failover è necessario forzare il servizio, pertanto potrebbero verificarsi perdite di dati.  
  
### <a name="to-turn-on-transaction-safety"></a>Per attivare la protezione delle transazioni  
  
1.  Connettersi al server principale.  
  
2.  Eseguire l'istruzione Transact-SQL seguente:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     dove *\<database>* è il nome del database con mirroring.  
  
### <a name="to-turn-off-transaction-safety"></a>Per disabilitare la protezione delle transazioni  
  
1.  Connettersi al server principale.  
  
2.  Eseguire l'istruzione seguente:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     dove *\<database>* è il database con mirroring.  
  
## <a name="see-also"></a>Vedere anche  
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
