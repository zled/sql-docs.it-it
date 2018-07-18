---
title: Using Reporting Services SOAP Headers (Uso di intestazioni SOAP di Reporting Services) | Microsoft Docs
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
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7a8a563b9265fa53e55c8625fd5123aa90cda23b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303641"
---
# <a name="using-reporting-services-soap-headers"></a>Utilizzo di intestazioni SOAP di Reporting Services
  La comunicazione con un metodo di servizio Web utilizzando SOAP segue un formato standard. Fanno parte di questo formato i dati codificati in un documento XML. Il documento XML è costituito da un elemento **Envelope** radice che a sua volta è costituito da un elemento **Body** obbligatorio e da un elemento **Header** facoltativo. L'elemento **Body** contiene i dati specifici del messaggio. L'elemento **Header** facoltativo può contenere informazioni aggiuntive non direttamente correlate al messaggio specifico. Ogni elemento figlio dell'elemento**Header** è definito intestazione SOAP.  
  
 Sebbene le intestazioni SOAP possano includere dati correlati al messaggio, contengono in genere informazioni elaborate dall'infrastruttura del server Web.  
  
 l servizio Web ReportServer definisce diverse classi da utilizzare nell'intestazione SOAP, ovvero <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> e <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Metodi di invio in batch](batching-methods.md)|Descrive come unire in batch più operazioni in una singola transazione utilizzando <xref:ReportService2005.BatchHeader>.|  
|[Identificazione dello stato di esecuzione](identifying-execution-state.md)|Descrive come gestire lo stato della sessione in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] tramite **SessionHeader**.|  
|[Impostazione dello spazio dei nomi degli elementi per il metodo GetProperties](setting-the-item-namespace-for-the-getproperties-method.md)|Descrive come recuperare le proprietà in base al percorso o all'ID di un elemento tramite il metodo <xref:ReportService2010.ReportingService2010.GetProperties%2A> e l'intestazione SOAP <xref:ReportService2010.ItemNamespaceHeader>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Guida di riferimento tecnico &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
