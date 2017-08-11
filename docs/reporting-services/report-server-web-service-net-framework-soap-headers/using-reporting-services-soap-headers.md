---
title: Con Reporting Services le intestazioni SOAP | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 08aec184077b69d05939fe493bf677043beb99d3
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="using-reporting-services-soap-headers"></a>Utilizzo di intestazioni SOAP di Reporting Services
  La comunicazione con un metodo di servizio Web utilizzando SOAP segue un formato standard. Fanno parte di questo formato i dati codificati in un documento XML. Il documento XML è costituito da una radice **busta** elemento, che a sua volta è costituito da un obbligatorio **corpo** elemento ed eventualmente **intestazione** elemento. Il **corpo** elemento contiene i dati specifici di un messaggio. Facoltativo **intestazione** elemento può contenere informazioni aggiuntive non direttamente correlate al messaggio specifico. Ogni elemento figlio del **intestazione** elemento viene chiamato un'intestazione SOAP.  
  
 Sebbene le intestazioni SOAP possano includere dati correlati al messaggio, contengono in genere informazioni elaborate dall'infrastruttura del server Web.  
  
 l servizio Web ReportServer definisce diverse classi da utilizzare nell'intestazione SOAP, ovvero <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> e <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Metodi di invio in batch](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md)|Descrive come unire in batch più operazioni in una singola transazione utilizzando <xref:ReportService2005.BatchHeader>.|  
|[Identificazione dello stato di esecuzione](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)|Viene descritto come gestire lo stato della sessione in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilizzando **SessionHeader**.|  
|[Impostazione di Namespace dell'elemento per il metodo GetProperties](../../reporting-services/report-server-web-service-net-framework-soap-headers/setting-the-item-namespace-for-the-getproperties-method.md)|Descrive come recuperare le proprietà in base al percorso o all'ID di un elemento tramite il metodo <xref:ReportService2010.ReportingService2010.GetProperties%2A> e l'intestazione SOAP <xref:ReportService2010.ItemNamespaceHeader>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
