---
title: Memorizzazione nella cache attiva (dimensioni) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 042214fa6f900921c7d66cb5824a68b0134ccbd2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067847"
---
# <a name="proactive-caching-dimensions"></a>Memorizzazione nella cache attiva (dimensioni)
  La memorizzazione nella cache attiva fornisce funzionalità automatiche di creazione e gestione della cache MOLAP per gli oggetti OLAP. I cubi incorporano immediatamente le modifiche apportate ai dati nel database, in base alle notifiche ricevute dal database. L'obiettivo della memorizzazione nella cache attiva consiste nel fornire le prestazioni della modalità MOLAP standard, garantendo l'immediatezza e la semplicità di gestione offerte da ROLAP.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> semplice è composto dalla specifica temporale e dalla notifica per la tabella. La specifica temporale definisce l'intervallo di tempo entro il quale eseguire l'aggiornamento della cache dopo la ricezione di una notifica di modifica. La notifica per la tabella definisce lo schema di notifica tra la tabella dati e l'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
