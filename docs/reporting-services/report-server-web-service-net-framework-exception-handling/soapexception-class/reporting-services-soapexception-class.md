---
title: Classe SoapException di Reporting Services | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
caps.latest.revision: "33"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 18fc1caebfceff356a28bfdfdf91d402d2bd6180
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="reporting-services-soapexception-class"></a>Classe SoapException di Reporting Services
  È necessario fornire una soluzione per errori specifici di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] che potrebbero verificarsi. In un'applicazione in cui viene chiesto all'utente di creare una cartella, l'utente potrebbe ad esempio tentare di creare una cartella che esiste già. Lo sviluppatore non dispone di controllo sull'immissione dell'utente nei campi relativi al nome e al percorso della cartella nell'applicazione, ma dispone di controllo sull'esperienza utente nel caso in cui si tenti accidentalmente di creare un elemento che esiste già.  
  
 Per semplificare l'individuazione di condizioni di errore specifiche, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifica un codice di errore per l'eccezione e restituisce la classificazione dell'errore usando le proprietà della classe **SoapException**. Per altre informazioni, vedere "Classe SoapException" nella documentazione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
 La tabella seguente elenca le proprietà pubbliche della classe **SoapException**.  
  
|Proprietà pubblica|Description|  
|---------------------|-----------------|  
|**Actor**|Codice che ha causato l'eccezione. Il valore è l'URL del metodo del servizio Web.|  
|**Detail**|Informazioni sull'errore specifiche dell'applicazione. Il valore viene impostato dal server di report ed è in formato XML. Per altre informazioni, vedere [Proprietà Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md) e [Uso della proprietà Detail per la gestione di errori specifici](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|URL o URN di un file della Guida associato all'errore. Il valore viene in genere impostato dal servizio Web e un URL viene impostato su Guida e supporto tecnico [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Poiché [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supporta più collegamenti alla Guida per gli errori che si verificano, il server di report imposta le informazioni sui collegamenti alla Guida come parte della proprietà **Detail**. Per altre informazioni, vedere [Elemento HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).|  
|**Message**|Messaggio descrittivo localizzato in cui viene descritto l'errore. Il testo può venire visualizzato nell'interfaccia utente dell'applicazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alla gestione delle eccezioni in Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Tabella degli errori SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
