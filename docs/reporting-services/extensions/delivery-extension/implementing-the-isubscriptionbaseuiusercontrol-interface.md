---
title: Implementazione dell'interfaccia ISubscriptionBaseUIUserControl | Documenti Microsoft
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
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 4e76edaa727df1694a5903e1cc9870c20581c9a0
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface"></a>Implementazione dell'interfaccia ISubscriptionBaseUIUserControl
  Le estensioni per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] possono contenere un'implementazione di un'interfaccia utente di sottoscrizione per la raccolta di informazioni specifiche dell'estensione in Gestione report. L'interfaccia utente viene richiamata quando un utente crea una nuova sottoscrizione o ne modifica una esistente. Quando viene creata una nuova sottoscrizione, nell'interfaccia utente vengono visualizzati i valori predefiniti appropriati e gli utenti possono interagire con il provider di recapito. Quando una sottoscrizione viene modificata, l'interfaccia utente viene prepopolata con le informazioni nella sottoscrizione corrente.  
  
 Le estensioni per il recapito forniscono un'interfaccia utente di sottoscrizione come controllo utente ASP.NET. Il server di report incorpora il controllo utente definito dall'estensione per il recapito quando viene visualizzata l'interfaccia utente di sottoscrizione. L'interfaccia di base che fornisce i metodi astratti che consentono di abilitare questa funzionalità è l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>. Questa interfaccia garantisce che le operazioni comuni, ad esempio la convalida di valori di input, vengano eseguite correttamente. Il controllo utente di base fornisce inoltre un set di proprietà predefinite utilizzate dal server di report per garantire coerenza tra le sottoscrizioni. Queste proprietà sono richieste dalle estensioni per il recapito integrate in Gestione report.  
  
 È possibile implementare l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> in un provider di recapito per compilare l'interfaccia utente di sottoscrizione per Gestione report. L'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> fornisce l'infrastruttura per consentire agli utenti di immettere i valori per le impostazioni di sottoscrizione, per l'elaborazione delle impostazioni necessarie per l'estensione per il recapito e per la convalida delle impostazioni.  
  
> [!NOTE]  
>  Non è necessario implementare l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> come parte dell'estensione per il recapito. Le sottoscrizioni che utilizzano l'estensione per il recapito possono invece essere sempre create tramite i metodi dell'API SOAP <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> e <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>. Per ulteriori informazioni sulle caratteristiche dell'API SOAP per la gestione sottoscrizione e recapito, vedere [Subscription and Delivery Methods](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md).  
  
 L'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> estende <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Il controllo utente che implementa <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> deve inoltre ereditare da **WebControl**. Per ulteriori informazioni sul **WebControl** classe, vedere il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] manuale dello sviluppatore.  
  
 Per un esempio di come utilizzare il <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interfaccia, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

