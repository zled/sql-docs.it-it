---
title: File dei log di traccia predefiniti disabilitati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 225c6ef4c82d21e1b2f8a11ea4da9b4ae73e68b9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064880"
---
# <a name="default-trace-log-files-disabled"></a>File dei log di traccia predefiniti disabilitati
  Questa regola consente di controllare il valore dell'opzione default trace enabled per la stored procedure sp_configure per determinare se la traccia predefinita sia impostata su ON (1) o OFF (0). Quando questa opzione è abilitata, la sessione di traccia predefinita fornisce informazioni sulla configurazione del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]e sulle modifiche a esso apportate. In alcuni casi, queste informazioni possono essere utili per gli utenti e per il Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../../includes/msconame-md.md)] durante la risoluzione dei problemi relativi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Utilizzare la stored procedure sp_configure per abilitare la traccia impostando il valore di default trace enabled su 1.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  