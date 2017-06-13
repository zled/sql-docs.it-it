---
title: Classe SoapException di Reporting Services | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3b19743906654dfcbfe6289181ae62b43a2df143
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-soapexception-class"></a>Classe SoapException di Reporting Services
  È necessario fornire una soluzione per errori specifici di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] che potrebbero verificarsi. In un'applicazione in cui viene chiesto all'utente di creare una cartella, l'utente potrebbe ad esempio tentare di creare una cartella che esiste già. Lo sviluppatore non dispone di controllo sull'immissione dell'utente nei campi relativi al nome e al percorso della cartella nell'applicazione, ma dispone di controllo sull'esperienza utente nel caso in cui si tenti accidentalmente di creare un elemento che esiste già.  
  
 Per semplificare le condizioni di errore specifico, intercettare [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifica un codice di errore per l'eccezione e restituisce la classificazione dell'errore utilizzando le proprietà di **SoapException** classe. Per ulteriori informazioni, vedere "Classe SoapException" nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentazione SDK.  
  
 Nella tabella seguente sono elencate le proprietà pubbliche del **SoapException** classe.  
  
|Proprietà pubblica|Description|  
|---------------------|-----------------|  
|**Attore**|Codice che ha causato l'eccezione. Il valore è l'URL del metodo del servizio Web.|  
|**Dettagli**|Informazioni sull'errore specifiche dell'applicazione. Il valore viene impostato dal server di report ed è in formato XML. Per ulteriori informazioni, vedere [proprietà Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md) e [utilizzando la proprietà Detail per gestire errori specifici](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|URL o URN di un file della Guida associato all'errore. Il valore viene in genere impostato dal servizio Web e un URL viene impostato su Guida e supporto tecnico [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Perché [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supporta più i collegamenti della Guida per gli errori che si verificano, il server di report imposta Guida le informazioni come parte del collegamento di **dettaglio** proprietà. Per ulteriori informazioni, vedere [elemento HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).|  
|**Message**|Messaggio descrittivo localizzato in cui viene descritto l'errore. Il testo può venire visualizzato nell'interfaccia utente dell'applicazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a gestione delle eccezioni in Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Tabella degli errori SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
