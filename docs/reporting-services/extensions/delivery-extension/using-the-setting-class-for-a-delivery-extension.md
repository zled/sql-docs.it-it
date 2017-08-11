---
title: Utilizzo della classe Setting per un'estensione di recapito | Documenti Microsoft
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
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e7be89798bb881fa189b2a902efb34cbfdc6b6ad
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Utilizzo della classe Setting per un'estensione per il recapito
  La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> si trova nello spazio dei nomi <xref:Microsoft.ReportingServices.Interfaces> e rappresenta le informazioni sulle impostazioni dell'estensione per un'estensione per il recapito. La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> fornisce l'infrastruttura per l'archiviazione delle informazioni relative alle impostazioni necessarie per il corretto funzionamento di un'estensione per il recapito. Per il recapito tramite posta elettronica in un server report, ad esempio, a un utente viene richiesto di fornire le impostazioni specifiche del recapito tramite posta elettronica, come l'indirizzo del destinatario, l'indirizzo del mittente, la riga dell'oggetto del messaggio di posta elettronica e altro ancora. Anche i provider di recapito personalizzati richiederanno senza dubbio che l'utente fornisca impostazioni specifiche per consentire il recapito di notifiche e report da parte dell'estensione per il recapito.  
  
 La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> viene utilizzata nell'implementazione della proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> dell'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> viene inoltre utilizzata per l'elaborazione dei dati di impostazione delle estensioni forniti da un utente quando viene creata una sottoscrizione o una notifica.  
  
 Per un esempio di come utilizzare il <xref:Microsoft.ReportingServices.Interfaces.Setting> classe, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
