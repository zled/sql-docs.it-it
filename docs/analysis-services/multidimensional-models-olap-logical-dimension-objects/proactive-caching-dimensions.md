---
title: La memorizzazione nella cache (dimensioni) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: 70624fe00b62733079aa0ffde47f8928cae0324d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="proactive-caching-dimensions"></a>Memorizzazione nella cache attiva (dimensioni)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]La memorizzazione nella cache fornisce la creazione automatica della cache MOLAP e la gestione per gli oggetti OLAP. I cubi incorporano immediatamente le modifiche apportate ai dati nel database, in base alle notifiche ricevute dal database. L'obiettivo della memorizzazione nella cache attiva consiste nel fornire le prestazioni della modalità MOLAP standard, garantendo l'immediatezza e la semplicità di gestione offerte da ROLAP.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> semplice è composto dalla specifica temporale e dalla notifica per la tabella. La specifica temporale definisce l'intervallo di tempo entro il quale eseguire l'aggiornamento della cache dopo la ricezione di una notifica di modifica. La notifica per la tabella definisce lo schema di notifica tra la tabella dati e l'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
