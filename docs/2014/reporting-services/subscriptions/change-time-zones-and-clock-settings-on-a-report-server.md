---
title: Modificare i fusi orari e le impostazioni dell'orologio in un server di report | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5157a079ec42264ef3f688e42b6ac294f2e54ef3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175150"
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a>Modificare i fusi orari e le impostazioni dell'orologio in un server di report
  Il server di report utilizza sempre il fuso orario del computer in cui è installato. Non è infatti possibile configurare un server di report in modo che utilizzi un fuso orario diverso. Se un'applicazione client punta a un server di report di un altro fuso orario, per eseguire un'operazione pianificata viene utilizzato il fuso orario del server di report. In Gestione report e nelle pagine di gestione di SharePoint il fuso orario è indicato in tutte le pagine di pianificazione, in modo che l'utente possa sapere esattamente quando verrà eseguita un'operazione pianificata. Ad esempio, nella pagina per la creazione di pianificazioni personalizzate verrà indicato "Il tempo è espresso in (UTC - 8.00 h) Pacifico (USA e Canada)".  
  
## <a name="changing-the-time-zone-native-mode"></a>Modifica del fuso orario (modalità nativa)  
 Se si modifica il fuso orario in un computer che ospita un server di report, è necessario riavviare il servizio del server di report affinché le modifiche apportate abbiano effetto.  
  
 I valori del timestamp degli snapshot della cronologia del report esistenti vengono sincronizzati sulla nuova impostazione del fuso orario. Se, ad esempio, è stato generato uno snapshot della cronologia di un report alle 9.00 e quindi si cambia il fuso orario impostando quello successivo, per lo snapshot generato verranno indicate le 10.00 e non più le 9.00. alle 10:00  
  
 Le pianificazioni conservano le impostazioni esistenti, ma ne viene eseguito il mapping al nuovo fuso orario. Se, ad esempio, l'esecuzione di una pianificazione è impostata per le 2.00 ora di Greenwich e si cambia il fuso orario impostando l'ora solare Europa occidentale, la pianificazione verrà eseguita alle 2.00 ora solare Europa occidentale.  
  
 I valori timestamp delle proprietà, ad esempio l'ora di creazione di una cartella o di un report collegato, non vengono sincronizzati rispetto a una nuova impostazione del fuso orario. Se si crea un report il 25 giugno alle ore 9.00 e quindi si reimposta il fuso orario o l'orologio, il timestamp continuerà a indicare il 25 giugno alle ore 9.00.  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a>Modifica del fuso orario (modalità SharePoint)  
 La configurazione del fuso orario per la modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene gestita nell'ambito delle impostazioni internazionali di SharePoint. Per altre informazioni, vedere [Regional settings (SharePoint Server 2010 (http://technet.microsoft.com/library/cc824907.aspx)](http://technet.microsoft.com/library/cc824907.aspx) (Impostazioni internazionali - SharePoint Server 2010).  
  
## <a name="changing-the-clock-settings"></a>Modifica delle impostazioni dell'orologio  
 La modifica dell'orologio del computer non ha alcun effetto sui valori timestamp esistenti. Se, ad esempio, si sposta l'orologio avanti di un'ora, i timestamp degli snapshot della cronologia dei report non cambiano. Può verificarsi un ritardo di 10 secondi prima che Elaborazione pianificazione e recapito utilizzi la nuova impostazione. Il ritardo effettivo può variare se sono state modificate le impostazioni dell'intervallo di polling nei file di configurazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare e arrestare il servizio Server di Report](../report-server/start-and-stop-the-report-server-service.md)   
 [Pianificazioni](schedules.md)  
  
  
