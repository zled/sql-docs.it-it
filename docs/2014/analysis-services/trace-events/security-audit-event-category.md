---
title: Categoria di eventi Security Audit | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d52589fc39376d5dfdfa3f540d3d1d47e89f448
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224241"
---
# <a name="security-audit-event-category"></a>Categoria di eventi Controllo di sicurezza
  La categoria di eventi Controllo di sicurezza include le classi di eventi descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Registra tutti i nuovi eventi di connessione generati dopo l'avvio della traccia, ad esempio quando un client richiede una connessione a un server in cui è in esecuzione un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Audit Logout|2|Registra tutti i nuovi eventi di disconnessione dall'avvio della traccia, ad esempio un client che esegue un comando di disconnessione.|  
|Audit Server Starts and Stops|4|Registra le attività di chiusura, avvio e sospensione dei servizi.|  
|Audit Object Permission Event|18|Registra tutte le modifiche alle autorizzazioni per gli oggetti.|  
|Audit Admin Operations Event|19|Registra operazioni del server per eseguire il backup, ripristinare, sincronizzazione, allegare, disconnettere, caricare immagini e salvare immagini.|  
  
 Per informazioni sulle colonne associate a ogni classe di evento inclusa nella categoria Controllo di sicurezza, vedere [Colonne di dati degli eventi di controllo di sicurezza](security-audit-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](analysis-services-trace-events.md)  
  
  
