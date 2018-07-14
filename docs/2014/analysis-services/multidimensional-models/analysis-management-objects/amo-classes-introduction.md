---
title: Introduzione a classi AMO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Management Objects]
- classes [AMO]
ms.assetid: d3c066bc-f812-4d53-9e96-9e306f2fc580
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb4e3761642f8b03e5853ae99e00cc4bc2f4a46f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328531"
---
# <a name="introducing-amo-classes"></a>Introduzione alle classi di AMO
  Analysis Management Objects (AMO) è una libreria di classi progettata per gestire un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] da un'applicazione client. Le classi AMO verranno utilizzate per amministrare gli oggetti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ad esempio database, dimensioni, cubi, strutture e modelli di data mining, ruoli e autorizzazioni, eccezioni e così via.  
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Classi esaminate negli argomenti sui concetti di AMO](../../../analysis-services/dev-guide/media/amo-reviewedclasses.gif "classi esaminate negli argomenti sui concetti di AMO")  
  
 La libreria AMO può essere considerata come un insieme di gruppi di oggetti correlati logicamente utilizzati per eseguire un'attività. Le classi AMO possono essere suddivise in categorie nel modo riportato di seguito. In questa sezione vengono trattati gli argomenti seguenti:  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classi fondamentali AMO](amo-fundamental-classes.md)|Descrive le classi necessarie per utilizzare qualsiasi altro set di classi.|  
|[Classi OLAP di AMO](amo-olap-classes.md)|Descrive le classi che consentono di gestire gli oggetti OLAP in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Classi di data mining AMO](amo-data-mining-classes.md)|Descrive le classi che consentono di gestire gli oggetti di data mining in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Classi di sicurezza AMO](amo-security-classes.md)|Descrive le classi che consentono di controllare l'accesso ad altri oggetti e di gestire la sicurezza.|  
|[Altre classi e altri metodi AMO](amo-other-classes-and-methods.md)|Descrive le classi e i metodi che consentono agli amministratori OLAP oppure ai responsabili delle operazioni di data mining di completare le attività giornaliere.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Architettura logica &#40;Analysis Services - dati multidimensionali&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40;Analysis Services - dati multidimensionali&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Sviluppo con Analysis Management Objects &#40;AMO&#41;](developing-with-analysis-management-objects-amo.md)  
  
  
