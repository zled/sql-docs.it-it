---
title: La memorizzazione nella cache (dimensioni) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4771869da2e8603cf09a5e579f358a408207e777
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="proactive-caching-dimensions"></a>Memorizzazione nella cache attiva (dimensioni)
  La memorizzazione nella cache attiva fornisce funzionalità automatiche di creazione e gestione della cache MOLAP per gli oggetti OLAP. I cubi incorporano immediatamente le modifiche apportate ai dati nel database, in base alle notifiche ricevute dal database. L'obiettivo della memorizzazione nella cache attiva consiste nel fornire le prestazioni della modalità MOLAP standard, garantendo l'immediatezza e la semplicità di gestione offerte da ROLAP.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> semplice è composto dalla specifica temporale e dalla notifica per la tabella. La specifica temporale definisce l'intervallo di tempo entro il quale eseguire l'aggiornamento della cache dopo la ricezione di una notifica di modifica. La notifica per la tabella definisce lo schema di notifica tra la tabella dati e l'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
