---
title: Rimozione di un'estensione per il rendering | Microsoft Docs
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
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c8ad34be5d818d70b8c46d82dbf348b9d0814824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055863"
---
# <a name="removing-a-rendering-extension"></a>Rimozione di un'estensione per il rendering
  Per rimuovere un [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] estensione per il rendering, rimuovere semplicemente la `Extension` elemento per l'estensione per il rendering dal file RSReportServer. config, che si trova **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Nome istanza > Services\ReportServer.** cartella. Se sono state create voci per una finestra di progettazione di Report, nonché un server di report, rimuovere il `Extension` elemento dal [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) anche. Dopo la rimozione delle informazioni di configurazione, l'estensione per il rendering non è più disponibile per il componente.  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione di Reporting Services](../../report-server/reporting-services-configuration-files.md)   
 [Implementazione di un'estensione per il rendering](implementing-a-rendering-extension.md)   
 [Panoramica delle estensioni per il rendering](rendering-extensions-overview.md)   
 [Implementazione dell'interfaccia IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Considerazioni sulla sicurezza per le estensioni](../security-considerations-for-extensions.md)   
 [Distribuzione di un'estensione per il rendering](deploying-a-rendering-extension.md)  
  
  