---
title: Distribuzione di un'estensione per l'elaborazione dati | Microsoft Docs
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4acfb4c0643a3bea2654b36027e4c6756ff28698
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="deploying-a-data-processing-extension"></a>Distribuzione di un'estensione per l'elaborazione dati
  Dopo avere scritto e compilato l'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] in una libreria [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], è necessario consentirne l'individuazione da parte del server di report e di Progettazione report. A tale scopo, è sufficiente copiare l'estensione nelle directory appropriate e aggiungere voci ai file di configurazione appropriati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="configuration-file-extension-element"></a>Elemento Extension del file di configurazione  
 Le estensioni per l'elaborazione dati distribuite nel server di report o in Progettazione report devono essere immesse come elementi **Extension** nei file di configurazione. Questi file sono RSReportServer.config per il server di report e RSReportDesigner.config per Progettazione report.  
  
 Nella tabella riportata di seguito vengono descritti gli attributi dell'elemento **Extension** per le estensioni per l'elaborazione dati.  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**Nome**|Nome univoco per l'estensione, ad esempio, "SQL" per l'estensione per l'elaborazione dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o "OLE DB" per l'estensione per l'elaborazione dati OLE DB. La lunghezza massima consentita per l'attributo **Name** è 255 caratteri. Il nome deve essere univoco tra tutte le voci dell'elemento **Extension** di un file di configurazione.|  
|**Tipo**|Elenco delimitato da virgole che include lo spazio dei nomi completo insieme al nome dell'assembly.|  
|**Visible**|Il valore **false** indica che l'estensione per l'elaborazione dati non deve essere visibile nelle interfacce utente. Se l'attributo non è incluso, il valore predefinito è **true**.|  
  
 Per altre informazioni sui file RSReportServer.config o RSReportDesigner.config, vedere [File di configurazione di Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Procedura: Distribuire un'estensione per l'elaborazione dati in un server di report](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-a-report-server.md)|Viene descritto come distribuire un'estensione per l'elaborazione dati in un server di report.|  
|[Procedura: Distribuire di un'estensione per l'elaborazione dati in Progettazione report](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)|Viene descritto come distribuire un'estensione per l'elaborazione dati in Progettazione report.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
