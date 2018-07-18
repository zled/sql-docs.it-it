---
title: Memorizzazione nella cache attiva (dimensioni) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9849f5ce2f82b44772a1faf360a530eb712c6dbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224571"
---
# <a name="proactive-caching-dimensions"></a>Memorizzazione nella cache attiva (dimensioni)
  La memorizzazione nella cache attiva fornisce funzionalità automatiche di creazione e gestione della cache MOLAP per gli oggetti OLAP. I cubi incorporano immediatamente le modifiche apportate ai dati nel database, in base alle notifiche ricevute dal database. L'obiettivo della memorizzazione nella cache attiva consiste nel fornire le prestazioni della modalità MOLAP standard, garantendo l'immediatezza e la semplicità di gestione offerte da ROLAP.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> semplice è composto dalla specifica temporale e dalla notifica per la tabella. La specifica temporale definisce l'intervallo di tempo entro il quale eseguire l'aggiornamento della cache dopo la ricezione di una notifica di modifica. La notifica per la tabella definisce lo schema di notifica tra la tabella dati e l'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
