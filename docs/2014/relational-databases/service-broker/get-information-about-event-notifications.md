---
title: Recuperare informazioni sulle notifiche degli eventi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f1632779e5e27387cd3eb5e04c105ddf2e04fa3c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276257"
---
# <a name="get-information-about-event-notifications"></a>Recupero di informazioni sulle notifiche degli eventi
  Le viste del catalogo seguenti sono disponibili per eseguire query sui metadati relative alle notifiche degli eventi.  
  
 **Per ottenere informazioni relative alle notifiche degli eventi non a livello di server**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Per visualizzare i metadati relativi a notifiche degli eventi in **sys.event_notifications** creati a livello del database, è almeno necessario disporre dell'autorizzazione CONTROL, ALTER, TAKE OWNERSHIP oppure VIEW DEFINITION sul database, essere proprietario della notifica degli eventi oppure disporre dell'autorizzazione ALTER ANY DATABASE EVENT NOTIFICATION. Per le notifiche degli eventi create in una coda specifica, è almeno necessario disporre dell'autorizzazione CONTROL, ALTER, TAKE OWNERSHIP oppure VIEW DEFINITION sull'oggetto, essere proprietario della notifica degli eventi oppure disporre dell'autorizzazione ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Per ottenere informazioni relative alle notifiche degli eventi a livello di server**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  È almeno necessario disporre dell'autorizzazione CONTROL o VIEW ANY DEFINITION sul server, essere dotati di accesso o essere il proprietario della notifica degli eventi oppure disporre dell'autorizzazione ALTER ANY EVENT NOTIFICATION per visualizzare i metadati relativi a eventuali notifiche degli eventi in **sys.server_event_notifications**.  
  
 **Per ottenere informazioni relative a tutti gli eventi che possono attivare notifiche degli eventi**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  Questa vista del catalogo non restituisce gruppi di eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Notifiche degli eventi](event-notifications.md)  
  
  
