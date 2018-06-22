---
title: Tipi di pubblicazioni per la replica transazionale | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 11e9e6ffafe62c66684470b4b04e2e0b67cc868b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062832"
---
# <a name="publication-types-for-transactional-replication"></a>Tipi di pubblicazioni per la replica transazionale
  La replica transazionale offre tre tipi di pubblicazioni:  
  
|Tipo di pubblicazione|Description|  
|----------------------|-----------------|  
|Pubblicazione transazionale standard|Appropriata per topologie in cui tutti i dati nel Sottoscrittore sono di sola lettura. (La replica transazionale non impone l'impostazione dei dati in sola lettura nel Sottoscrittore).<br /><br /> Le pubblicazioni transazionali standard vengono create per impostazione predefinita quando si utilizzano Transact-SQL o gli oggetti RMO (Replication Management Objects). Quando si utilizza la Creazione guidata nuova pubblicazione, tali pubblicazioni vengono create selezionando **Pubblicazione transazionale** nella pagina **Tipo di pubblicazione** .<br /><br /> Per altre informazioni sulla creazione di pubblicazioni, vedere [Pubblicare dati e oggetti di database](../publish/publish-data-and-database-objects.md).|  
|Pubblicazione transazionale in una topologia peer-to-peer|Le caratteristiche di questo tipo di pubblicazione sono:<br /><br /> Ogni posizione presenta dati identici e opera sia come server di pubblicazione che come Sottoscrittore.<br /><br /> La stessa riga può essere modificata solo in una posizione per volta.<br /><br /> Questa topologia è più adatta agli ambienti server che necessitano di disponibilità elevata e di scalabilità per la lettura.<br /><br /> <br /><br /> Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica transazionale](transactional-replication.md)  
  
  