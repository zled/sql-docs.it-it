---
title: "Proprietà di Reporting Services | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 1e6abe6453acbe4102de8a2973668b6cf59dfcc1
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="reporting-services-properties"></a>Proprietà di Reporting Services
  Il server di report definisce un set di proprietà di sistema globali del server di report e un set di proprietà degli elementi associate a un singolo elemento archiviato nel database del server di report. Le proprietà definite dal server di report non possono essere eliminate e in alcuni casi sono di sola lettura. Un'applicazione consente di estendere le proprietà di sistema e degli elementi aggiungendo a queste proprietà ulteriori proprietà definite dall'utente.  
  
 I seguenti metodi di servizio Web di recuperare e impostare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] proprietà.  
  
|Metodo|Azione|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Restituisce i valori di una o più proprietà di un elemento nel database del server di report.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Restituisce una o più proprietà di sistema.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Imposta una o più proprietà di un elemento nel database del server di report.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Imposta una o più proprietà di sistema.|  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Elemento proprietà Server di report](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Vengono descritte le proprietà specifiche degli elementi in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Proprietà di sistema di Server di report](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Vengono descritte le proprietà di sistema in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
