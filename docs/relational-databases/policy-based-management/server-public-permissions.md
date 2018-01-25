---
title: Autorizzazioni server per il ruolo public | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: "11"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3653a2895d4a2ce514a5f278a173ba8775dade6f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="server-public-permissions"></a>Autorizzazioni server per il ruolo public
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questa regola determina se il ruolo del server public ha autorizzazioni server. Ogni account di accesso creato nel server è un membro del ruolo del server public. Se questa condizione viene soddisfatta, ogni account di accesso nel server disporrà di autorizzazioni server.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Non concedere autorizzazioni server al ruolo del server public.  
  
> [!IMPORTANT]  
>  Una volta completata l'installazione, nel ruolo **PUBLIC** è disponibile l'autorizzazione **CONNECT** per tutti gli endpoint ad eccezione di **Connessione amministrativa dedicata**. Questa situazione è normale e, generalmente, non deve essere modificata (l'accesso viene controllato con l'autorizzazione **CONNECT SQL** che viene concessa automaticamente in caso di creazione di nuovi account di accesso).  
  
### <a name="for-more-information"></a>Per ulteriori informazioni  
 [Sicurezza di SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
