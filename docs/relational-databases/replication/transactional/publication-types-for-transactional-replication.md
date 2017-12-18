---
title: Tipi di pubblicazioni per la replica transazionale | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ae2a1a2db15c7a7d1a80df8fbd8a711e107d8d0d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="publication-types-for-transactional-replication"></a>Tipi di pubblicazioni per la replica transazionale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La replica transazionale offre tre tipi di pubblicazioni:  
  
|Tipo di pubblicazione|Descrizione|  
|----------------------|-----------------|  
|Pubblicazione transazionale standard|Appropriata per topologie in cui tutti i dati nel Sottoscrittore sono di sola lettura. (La replica transazionale non impone l'impostazione dei dati in sola lettura nel Sottoscrittore).<br /><br /> Le pubblicazioni transazionali standard vengono create per impostazione predefinita quando si utilizzano Transact-SQL o gli oggetti RMO (Replication Management Objects). Quando si utilizza la Creazione guidata nuova pubblicazione, tali pubblicazioni vengono create selezionando **Pubblicazione transazionale** nella pagina **Tipo di pubblicazione** .<br /><br /> Per altre informazioni sulla creazione di pubblicazioni, vedere [Pubblicare dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).|  
|Pubblicazione transazionale in una topologia peer-to-peer|Le caratteristiche di questo tipo di pubblicazione sono:<br /><br /> - Ogni posizione presenta dati identici e opera sia come server di pubblicazione che come Sottoscrittore.<br /><br /> - La stessa riga può essere modificata solo in una posizione per volta.<br /><br /> - Questa topologia è più adatta agli ambienti server che necessitano di disponibilità elevata e di scalabilità per la lettura.<br /><br /> <br /><br /> Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica transazionale](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
