---
title: Rimozione di un'estensione per il Rendering | Documenti Microsoft
ms.custom: 
ms.date: 03/18/2017
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
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ea37cf7ac15504a00aeb0f1379e9d48a71231e1c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="removing-a-rendering-extension"></a>Rimozione di un'estensione per il rendering
  Per rimuovere un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] estensione per il rendering, rimuovere semplicemente la **estensione** elemento per l'estensione per il rendering dal file RSReportServer. config, situato **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Nome istanza > Services\ReportServer.** cartella. Se sono state create voci per una finestra di progettazione di Report, nonché un server di report, rimuovere il **estensione** elemento il [File di configurazione RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md) anche. Dopo la rimozione delle informazioni di configurazione, l'estensione per il rendering non è più disponibile per il componente.  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione di Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Implementazione di un'estensione per il Rendering](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Cenni preliminari sulle estensioni di rendering](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Implementazione dell'interfaccia IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Considerazioni sulla sicurezza per le estensioni](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Distribuzione di un'estensione per il rendering](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
