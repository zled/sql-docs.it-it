---
title: Estensioni di Reporting Services | Documenti Microsoft
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
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
caps.latest.revision: 45
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: cd4cd15bf03648329dab8bc7ef55314ece7cf9a2
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="reporting-services-extensions"></a>Estensioni di Reporting Services
  L'architettura modulare di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è progettata per offrire estendibilità. È disponibile un'API in codice gestito che consente di sviluppare, installare e gestire in modo semplice le estensioni usate da numerosi componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. È possibile creare private o assembly condivisi utilizzando il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] e aggiungere nuove [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] funzionalità per soddisfare le esigenze aziendali in continua evoluzione.  
  
 L'architettura unica di estendibilità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consente agli sviluppatori di estendere caratteristiche specifiche del prodotto e dei relativi componenti. Attualmente, è disponibile ampio supporto per l'estensione delle funzionalità di elaborazione dati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. L'API di elaborazione dati include convenzioni e costrutti del provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] comuni che consentono agli sviluppatori di compilare funzionalità aggiuntive di elaborazione dati in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Queste estensioni per l'elaborazione dati aggiungono funzionalità sia al server di report che a Progettazione report e consentono una perfetta integrazione dei dati personalizzati nei report.  
  
 Un'altra estensione supportata è quella per il recapito. L'API di recapito è completamente integrata nell'architettura di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] e consente l'utilizzo di un'ampia gamma di meccanismi di recapito per l'invio di notifiche dei report agli utenti. È possibile estendere il server di report per offrire agli utenti recapito personalizzato, nonché estendere le pagine di gestione delle sottoscrizioni di Gestione report per consentite l'utilizzo di estensioni per il recapito personalizzate per le sottoscrizioni.  
  
 Un'altra estensione del server di report, RDCE (Report Definition Customization Extension) consente di personalizzare in modo dinamico la definizione di un report prima che venga passata al motore di elaborazione. È possibile personalizzare i report in base a fattori come gli utenti o le lingue. È ad esempio possibile implementare viste diverse per utenti diversi, ad esempio amministratori o membri di un reparto, oppure personalizzare un report con layout diversi a seconda che ne venga eseguito il rendering in francese o in arabo.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Considerazioni sulla sicurezza per le estensioni](../../reporting-services/extensions/security-considerations-for-extensions.md)  
 Vengono descritti i problemi di sicurezza relativi allo sviluppo e alla distribuzione delle estensioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementazione di un'estensione per l'elaborazione dati](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)  
 Vengono descritti i requisiti e i passaggi per l'implementazione di un'estensione per l'elaborazione dati per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementazione di un'estensione di recapito](../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)  
 Vengono descritti i requisiti e i passaggi per l'implementazione di un'estensione per il recapito per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementazione di un'estensione per il Rendering](../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)  
 Viene fornita un'introduzione allo sviluppo delle estensioni per il rendering.  
  
 [Implementazione di un'estensione di sicurezza](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)  
 Vengono descritti i requisiti e i passaggi per l'implementazione di un'estensione di sicurezza di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Libreria di estensioni di Reporting Services](../../reporting-services/extensions/reporting-services-extension-library.md)  
 Vengono forniti riferimenti per la programmazione per la libreria di API di estensione per le caratteristiche di estendibilità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
  
