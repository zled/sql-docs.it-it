---
title: Risoluzione dei problemi di aggiornamento | Documenti Microsoft
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
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6072fb3c1d52048832bd6d07f34828c84eb2d491
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068395"
---
# <a name="resolving-upgrade-issues"></a>Risoluzione dei problemi di aggiornamento
  Negli argomenti di questa sezione vengono descritti i problemi relativi all'aggiornamento rilevabili e quelli non rilevabili che possono tuttavia influire sull'esecuzione dell'aggiornamento o del post-aggiornamento. I problemi sono organizzati per componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Problemi di aggiornamento più recenti](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Problemi di aggiornamento della ricerca full-Text](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Problemi di aggiornamento della replica](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Problemi di aggiornamento di SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Problemi che impediscono l'aggiornamento  
 Alcune configurazioni o impostazioni di una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono impedire l'esecuzione dell'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Se il programma di installazione rileva questi problemi durante l'installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il processo di aggiornamento viene arrestato e all'utente viene richiesto di eseguire Preparazione di aggiornamento e di risolvere i problemi che bloccano l'installazione.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Se le attività seguenti sono elencate nel report di aggiornamento del [!INCLUDE[ssDE](../../includes/ssde-md.md)], è necessario eseguire le azioni richieste prima dell'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
-   [Scollegare il database con ID 32767](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Rinominare gli account di accesso corrispondenti i nomi dei ruoli predefiniti del server](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Rinominare l'utente sys](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [Utilizzare sp_rename per rinominare il nome di indice duplicati](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
