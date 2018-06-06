---
title: Database indipendenti con Gruppi di disponibilità Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8226893f960bd0c1b64c589219121f323226766d
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768647"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>Database indipendenti con Gruppi di disponibilità Always On (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In questo argomento vengono fornite informazioni sull'utilizzo di un database indipendente con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   [Prerequisiti](#Prerequisites)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> Prerequisiti  
  
-   Prima di aggiungere un database indipendente a un gruppo di disponibilità, verificare che l'opzione del server **contained database authentication** sia impostata su **1** in ogni istanza del server in cui è ospitata una replica di disponibilità per il gruppo di disponibilità. Per altre informazioni, vedere [Opzione di configurazione del server contained database authentication](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) e [Opzioni di configurazione del server &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Opzioni di configurazione del server &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Database indipendenti](../../../relational-databases/databases/contained-databases.md)  
  
  
