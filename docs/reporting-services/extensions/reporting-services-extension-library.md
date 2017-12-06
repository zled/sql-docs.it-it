---
title: Libreria di estensioni di Reporting Services | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: "33"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 921ccbecb3f711daba1b87a8f01a97f903935cf2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="reporting-services-extension-library"></a>Libreria di estensioni di Reporting Services
  La libreria di estensioni di Reporting Services è un set di classi, interfacce e tipi di valori inclusi in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Questa libreria consente di accedere alle funzionalità di sistema ed è progettata come base per l'uso di applicazioni [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] per l'estensione dei componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="namespaces"></a>Spazi dei nomi  
 La libreria di estensioni [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fornisce gli spazi dei nomi seguenti.  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 Contiene classi e interfacce che consentono di compilare componenti che estendono le funzionalità di elaborazione dati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 Contiene classi e interfacce che consentono di costruire notifiche personalizzate e di inviarle agli utenti tramite estensioni per il recapito personalizzate, nonché di compilare estensioni di sicurezza personalizzate per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 **Microsoft.ReportingServices.ReportRendering**  
 Contiene classi e interfacce che consentono di estendere le funzionalità di rendering di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Utilizzando i membri di questo spazio dei nomi con i membri dello spazio dei nomi <xref:Microsoft.ReportingServices.Interfaces>, è possibile compilare estensioni per il rendering personalizzate per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)  
  
  
