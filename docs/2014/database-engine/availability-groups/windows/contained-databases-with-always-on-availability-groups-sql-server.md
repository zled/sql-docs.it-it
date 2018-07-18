---
title: Database indipendenti con Gruppi di disponibilità Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5086a557319d4db305f4a3d5d6c2df6437e3f8c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285707"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>Database indipendenti con Gruppi di disponibilità Always On (SQL Server)
  In questo argomento vengono fornite informazioni sull'utilizzo di un database indipendente con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   [Prerequisiti](#Prerequisites)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> Prerequisiti  
  
-   Prima di aggiungere un database indipendente a un gruppo di disponibilità, verificare che l'opzione del server `contained database authentication` sia impostata su `1` in ogni istanza del server in cui è ospitata una replica di disponibilità per il gruppo di disponibilità. Per altre informazioni, vedere [Opzione di configurazione del server contained database authentication](../../configure-windows/contained-database-authentication-server-configuration-option.md) e [Opzioni di configurazione del server &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Opzioni di configurazione del server &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Database indipendenti](../../../relational-databases/databases/contained-databases.md)  
  
  
