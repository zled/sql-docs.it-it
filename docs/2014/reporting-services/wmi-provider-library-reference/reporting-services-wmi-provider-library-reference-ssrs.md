---
title: Riferimento della libreria del provider WMI Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e5f5958b52e59f3eb741f0f593a49e865dfb300e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217931"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Riferimento della libreria del provider WMI Reporting Services (SSRS)
  Il provider WMI (Windows Management Instrumentation) di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporta operazioni WMI che consentono di scrivere script e codice per modificare le impostazioni del server di report e di Gestione report.  
  
 Ad esempio, se si vuole modificare l'impostazione relativa all'uso della sicurezza integrata quando il server di report si connette al database del server di report, creare un'istanza della classe MSReportServer_ConfigurationSetting e usare la proprietà DatabaseIntegratedSecurity dell'istanza del server di report. Le classi mostrate nella tabella seguente rappresentano i componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le classi sono definite negli spazi dei nomi [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] o [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] . Ognuna delle classi supporta operazioni di lettura e scrittura. Le operazioni di creazione non sono supportate.  
  
## <a name="classes"></a>Classi  
 [Classe MSReportServer_Instance](msreportserver-instance-class.md)  
 Fornisce le informazioni di base necessarie affinché un client si connetta a un server di report installato.  
  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
 Rappresenta i parametri di installazione e di runtime di un'istanza del server di report. Tali parametri sono archiviati nel file di configurazione per il server di report.  
  
 Per altre informazioni sulle operazioni WMI, vedere la documentazione di WMI SDK inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere al provider WMI per Reporting Services](../tools/access-the-reporting-services-wmi-provider.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
