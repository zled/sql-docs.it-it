---
title: Avviare SQL Server con la configurazione minima | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a5113a3ce8cebae81ccd8ba63cb6b92abc67896e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298917"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Avvio di SQL Server con la configurazione minima
  In caso di problemi di configurazione che impediscono l'avvio del server, è possibile avviare un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando la configurazione minima. Si tratta dell'opzione di avvio **-f**. L'avvio di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la configurazione minima comporta l'attivazione automatica della modalità utente singolo per il server.  
  
 Quando si avvia un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la configurazione minima, si noti quanto segue:  
  
-   La connessione è consentita a un solo utente e il processo CHECKPOINT non viene eseguito.  
  
-   L'accesso remoto e il read-ahead sono disabilitati.  
  
-   Le stored procedure di avvio non vengono eseguite.  
  
 Dopo aver avviato il server con la configurazione minima, è necessario modificare il valore o i valori delle opzioni del server appropriati e quindi arrestare e riavviare il server.  
  
> [!IMPORTANT]  
>  Usare l'utilità **sqlcmd** e la connessione amministrativa dedicata (DAC) per eseguire la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si utilizza una connessione normale, arrestare il servizio SQL Server Agent prima di connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità configurazione minima. In caso contrario, il servizio SQL Server Agent utilizzerà la connessione, bloccandola.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio, arresto o sospensione del servizio SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Connessione di diagnostica per gli amministratori di database](diagnostic-connection-for-database-administrators.md)   
 [Utilità sqlcmd](../../tools/sqlcmd-utility.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Opzioni di avvio del servizio del motore di database](database-engine-service-startup-options.md)  
  
  
