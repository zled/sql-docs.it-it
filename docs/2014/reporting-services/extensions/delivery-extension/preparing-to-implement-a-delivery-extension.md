---
title: Preparazione all'implementazione di un'estensione per il recapito | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1f03d017d7e154a77baa1da47905c8badf256bbb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055189"
---
# <a name="preparing-to-implement-a-delivery-extension"></a>Preparazione all'implementazione di un'estensione per il recapito
  Prima di implementare l'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], è necessario definire le interfacce da implementare. È innanzitutto necessario stabilire in che modo verrà utilizzata l'estensione per il recapito, quali impostazioni sono necessarie per l'estensione per il recapito e le funzionalità specifiche da implementare per il recapito delle notifiche dei report.  
  
 Ogni estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] deve fornire le funzionalità seguenti:  
  
-   Un'implementazione dell'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IExtension> che rappresenta l'estensione e un nome di estensione localizzato.  
  
-   Un'implementazione di <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> che crea un'estensione per il recapito che può essere utilizzata per recapitare notifiche dei report agli utenti finali.  
  
-   La possibilità di elaborare dati utente specifici per una sottoscrizione.  
  
 Ogni estensione per il recapito può essere estesa per includere la funzionalità seguente:  
  
-   Un'implementazione del controllo utente [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] che consente agli utenti finali di utilizzare Gestione report per creare sottoscrizioni dei report che utilizzano l'estensione per il recapito.  
  
 Nella tabella seguente sono descritte le interfacce e le classi disponibili per le estensioni per il recapito.  
  
|Interfaccia o classe|Description|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> Interfaccia|Rappresenta un'estensione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Interfaccia|Rappresenta un'estensione per il recapito in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Interfaccia|Contiene informazioni sul server di report richieste dalle estensioni per il recapito (ad esempio, un elenco delle estensioni per il rendering disponibili).|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.Setting>|Rappresenta un'impostazione per un'estensione.|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.Notification>|Contiene informazioni sulle sottoscrizioni utilizzate dalle estensioni per il recapito dei report.|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.Report>|Rappresenta informazioni e metodi specifici del report che consentono alle estensioni per il recapito di recapitare i report agli utenti.|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>|Rappresenta l'output di un'estensione per il rendering. Un oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> contiene il nome file associato e le informazioni sul tipo richiesti dall'estensione per il recapito per elaborare il flusso restituito dall'estensione per il rendering.|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Interfaccia|Controllo utente che rappresenta il mezzo per il recupero delle informazioni sulla sottoscrizione specifiche dell'estensione dall'utente in Gestione report (ad esempio, un indirizzo di posta elettronica o il percorso di una condivisione file).|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../reporting-services-extensions.md)   
 [Implementazione di un'estensione per il recapito](implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  