---
title: Distribuzione di un'estensione per l'elaborazione dati | Microsoft Docs
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
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 63628c1be1803833a65875ddf75d4434af38c87f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167200"
---
# <a name="deploying-a-data-processing-extension"></a>Distribuzione di un'estensione per l'elaborazione dati
  Dopo avere scritto e compilato l'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] in una libreria [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], è necessario consentirne l'individuazione da parte del server di report e di Progettazione report. A tale scopo, è sufficiente copiare l'estensione nelle directory appropriate e aggiungere voci ai file di configurazione appropriati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="configuration-file-extension-element"></a>Elemento Extension del file di configurazione  
 Le estensioni per l'elaborazione dati distribuite nel server di report o in Progettazione report devono essere immesse come elementi **Extension** nei file di configurazione. Questi file sono RSReportServer.config per il server di report e RSReportDesigner.config per Progettazione report.  
  
 Nella tabella riportata di seguito vengono descritti gli attributi dell'elemento **Extension** per le estensioni per l'elaborazione dati.  
  
|attribute|Description|  
|---------------|-----------------|  
|`Name`|Nome univoco per l'estensione, ad esempio, "SQL" per l'estensione per l'elaborazione dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o "OLE DB" per l'estensione per l'elaborazione dati OLE DB. La lunghezza massima consentita per l'attributo `Name` è di 255 caratteri. Il nome deve essere univoco tra tutte le voci dell'elemento **Extension** di un file di configurazione.|  
|`Type`|Elenco delimitato da virgole che include lo spazio dei nomi completo insieme al nome dell'assembly.|  
|`Visible`|Il valore `false` indica che l'estensione per l'elaborazione dati non deve essere visibile nelle interfacce utente. Se l'attributo non è incluso, il valore predefinito è `true`.|  
  
 Per altre informazioni sui file RSReportServer.config o RSReportDesigner.config, vedere [File di configurazione di Reporting Services](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Procedura: Distribuire un'estensione per l'elaborazione dati in un server di report](deploying-a-data-processing-extension-to-a-report-server.md)|Viene descritto come distribuire un'estensione per l'elaborazione dati in un server di report.|  
|[Procedura: Distribuire di un'estensione per l'elaborazione dati in Progettazione report](deploying-a-data-processing-extension-to-report-designer.md)|Viene descritto come distribuire un'estensione per l'elaborazione dati in Progettazione report.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  