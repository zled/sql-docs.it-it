---
title: Categoria di eventi di controllo di sicurezza | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1d4136c84692e1e2a171a11c867598a7b2c51c34
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="security-audit-event-category"></a>Categoria di eventi Controllo di sicurezza
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi Controllo di sicurezza include le classi di eventi descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Registra tutti i nuovi eventi di connessione generati dopo l'avvio della traccia, ad esempio quando un client richiede una connessione a un server in cui è in esecuzione un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Audit Logout|2|Registra tutti i nuovi eventi di disconnessione dall'avvio della traccia, ad esempio un client che esegue un comando di disconnessione.|  
|Audit Server Starts and Stops|4|Registra le attività di chiusura, avvio e sospensione dei servizi.|  
|Audit Object Permission Event|18|Registra tutte le modifiche alle autorizzazioni per gli oggetti.|  
|Audit Admin Operations Event|19|Registra operazioni del server per eseguire il backup, ripristinare, sincronizzazione, allegare, disconnettere, caricare immagini e salvare immagini.|  
  
 Per informazioni sulle colonne associate a ogni classe di evento inclusa nella categoria Controllo di sicurezza, vedere [Colonne di dati degli eventi di controllo di sicurezza](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
