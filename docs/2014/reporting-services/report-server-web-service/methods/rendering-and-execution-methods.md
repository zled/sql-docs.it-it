---
title: Metodi di rendering e di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bd1745f845cda954c0e447a8a1d035646fd298dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156848"
---
# <a name="rendering-and-execution-methods"></a>Metodi di rendering e di esecuzione
  Per gestire l'esecuzione, il rendering e la memorizzazione nella cache degli elementi, è possibile utilizzare i metodi seguenti.  
  
|Metodo|Azione|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|Invalida la cache per un elemento.|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|Restituisce la configurazione della cache per un elemento e le impostazioni che indicano la scadenza della copia dell'elemento memorizzata nella cache.|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|Restituisce l'opzione di esecuzione e le impostazioni associate per un singolo elemento.|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|Restituisce un elenco di impostazioni di esecuzione supportate.|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|Elabora il report specificato e ne esegue il rendering in un formato specificato.|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|Configura un elemento per la memorizzazione nella cache e fornisce le impostazioni che specificano il momento in cui scade la copia memorizzata nella cache dell'elemento.|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|Imposta le opzioni di esecuzione e le proprietà di esecuzione associate per un singolo elemento.|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|Genera uno snapshot di esecuzione per un elemento specificato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../report-server-web-service.md)   
 [Metodi del servizio Web ReportServer](report-server-web-service-methods.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  