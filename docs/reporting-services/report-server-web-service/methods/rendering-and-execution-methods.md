---
title: Metodi di rendering e di esecuzione | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0fcd2398f2f02814d435ab1d611f139ebe5de181
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779249"
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
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Metodi del servizio Web ReportServer](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
