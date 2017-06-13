---
title: Implementazione di un&quot;estensione di recapito | Documenti Microsoft
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
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9909a4711eb5b1ffde9b865411bd552e6b409bc6
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-a-delivery-extension"></a>Implementazione di un'estensione per il recapito
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] consente agli utenti di creare e pubblicare report che, una volta creati e pubblicati, possono essere recapitati in diverse posizioni. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] include inoltre diverse estensioni per il recapito e un'API di recapito tramite cui gli sviluppatori possono creare estensioni per il recapito aggiuntive per estendere ulteriormente le funzionalità di recapito in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Per un esempio di implementazione di un'estensione di recapito, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Cenni preliminari sulle estensioni di recapito](../../../reporting-services/extensions/delivery-extension/delivery-extensions-overview.md)  
 Vengono fornite informazioni introduttive per la scrittura di un'estensione per il recapito personalizzata per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Preparazione all'implementazione di un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/preparing-to-implement-a-delivery-extension.md)  
 Vengono descritte le interfacce e le classi disponibili per l'implementazione di un'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], nonché i problemi da considerare prima dell'implementazione.  
  
 [Creazione di una libreria di estensioni di recapito](../../../reporting-services/extensions/delivery-extension/creating-a-delivery-extension-library.md)  
 Vengono descritte le operazioni di assegnazione di uno spazio dei nomi per l'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e di compilazione dell'estensione per il recapito nella DLL di una libreria.  
  
 [Implementazione dell'interfaccia IDeliveryExtension per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Vengono descritti gli attributi di un'estensione per il recapito e come implementare una classe personalizzata dell'estensione per il recapito.  
  
 [Utilizzo della classe Notification per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/using-a-notification-class-for-a-delivery-extension.md)  
 Vengono descritti gli attributi di un **notifica** classe e come utilizzarla nell'implementazione dell'estensione di recapito.  
  
 [Utilizzo della classe Setting per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/using-the-setting-class-for-a-delivery-extension.md)  
 Vengono descritti gli attributi di un **impostazione** classe e come utilizzarla nell'implementazione dell'estensione di recapito.  
  
 [Utilizzo dell'interfaccia IDeliveryReportServerInformation per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 Vengono descritti gli attributi di un **IDeliveryReportServerInformation** interfaccia e come utilizzarla nell'implementazione dell'estensione di recapito.  
  
 [Utilizzo della classe di Report per l'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md)  
 Vengono descritti gli attributi di un **Report** classe e come utilizzarla nell'implementazione dell'estensione di recapito.  
  
 [Utilizzo della classe RenderedOutputFile per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Vengono descritti gli attributi di un **RenderedOutputFile** classe e come utilizzarla nell'implementazione dell'estensione di recapito.  
  
 [Implementazione dell'interfaccia ISubscriptionBaseUIUserControl per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 Vengono descritti gli attributi di un controllo utente di un'estensione per il recapito e come implementare un'interfaccia utente personalizzata per una sottoscrizione.  
  
 [Distribuzione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
 Viene descritto come distribuire un'estensione per il recapito.  
  
 [Debug del codice di estensione di recapito](../../../reporting-services/extensions/delivery-extension/debugging-delivery-extension-code.md)  
 Viene descritto come eseguire il debug del codice in un'estensione per il recapito.  
  
 [Rimozione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/removing-a-delivery-extension.md)  
 Viene descritto come rimuovere un'estensione per il recapito da un server di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
