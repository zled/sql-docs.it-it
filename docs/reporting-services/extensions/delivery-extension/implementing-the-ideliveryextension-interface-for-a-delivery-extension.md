---
title: Implementazione dell'interfaccia IDeliveryExtension per un'estensione di recapito | Documenti Microsoft
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
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
caps.latest.revision: 37
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 82bf0172d2ad744d5a34945596814cd584888d95
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a>Implementazione dell'interfaccia IDeliveryExtension per un'estensione per il recapito
  La classe di estensioni per il recapito viene utilizzata per recapitare le notifiche dei report agli utenti in base al contenuto delle notifiche. La classe di estensioni per il recapito fornisce anche l'infrastruttura per la convalida delle impostazioni utente passate all'estensione per il recapito. Questa classe deve inoltre contenere proprietà specifiche che i client possono utilizzare per ottenere informazioni sul nome dell'estensione, sulle impostazioni supportate dall'estensione e sui formati di rendering disponibili per l'estensione per il recapito.  
  
 ![Processo dell'interfaccia IDeliveryExtension](../../../reporting-services/extensions/delivery-extension/media/bk-ext-02.gif "IDeliveryExtension interface process")  
L'interfaccia IDeliveryExtension consente la convalida dei dati utente e fornisce ai client informazioni sulle impostazioni di recapito necessarie  
  
 Per creare un'estensione per il recapito, implementare <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> e <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Il **IDeliveryExtension** interfaccia consente l'estensione per il recapito recapitare notifiche dei report utilizzando il <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> (metodo) e per convalidare le impostazioni di estensione in ingresso tramite il <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> metodo. Il **IExtension** interfaccia consente l'estensione per il recapito di implementare un nome di estensione localizzato e di elaborare le informazioni di configurazione specifiche dell'estensione archiviate nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] file di configurazione. Implementando **IExtension**, contiene l'estensione per il recapito di <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> proprietà. È consigliabile che [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] supporto delle estensioni di recapito di **LocalizedName** proprietà, in modo che gli utenti riscontrano un nome familiare per l'estensione in un'interfaccia utente, ad esempio Gestione Report.  
  
 Estensione per il recapito deve implementare anche il **ExtensionSettings** proprietà del **IDeliveryExtension** interfaccia. Il server di report utilizza il valore restituito dalla proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> per valutare le impostazioni necessarie per un'estensione per il recapito. I client che interagiscono con le estensioni per il recapito utilizzano il metodo <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> del servizio Web ReportServer per restituire un elenco di impostazioni per l'estensione per il recapito.  
  
 È inoltre possibile utilizzare la classe di estensioni per il recapito per recuperare ed elaborare i dati di configurazione personalizzati archiviati nel file RSReportServer.config. Per ulteriori informazioni sull'elaborazione dei dati di configurazione personalizzati, vedere il metodo <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Per un esempio **IDeliveryExtension** implementazione della classe, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
