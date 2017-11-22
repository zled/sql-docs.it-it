---
title: Architettura logica (Analysis Services - dati multidimensionali) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 454dddc6914853bf202376c47a1c929a0df4a6ac
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Informazioni sull'architettura logica di Microsoft OLAP
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza i componenti server e client per fornire l'elaborazione analitica online (OLAP) e funzionalità di data mining per applicazioni di business intelligence:  
  
-   Il componente server di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene implementato come un servizio di Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta più istanze nello stesso computer, con ogni istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementato come un'istanza separata del servizio Windows.  
  
-   I client comunicano con [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mediante lo standard pubblico XML for Analysis (XMLA), un protocollo basato su SOAP per l'esecuzione di comandi e la ricezione di risposte che viene esposto come un servizio Web. Tramite XMLA vengono inoltre offerti modelli a oggetti client a cui è possibile accedere usando un provider gestito, ad esempio ADOMD.NET, o un provider OLE DB nativo.  
  
-   I comandi di query possono essere eseguiti tramite i linguaggi seguenti: SQL, MDX (Multidimensional Expressions), un linguaggio di query standard del settore per l'analisi, o DMX (Data Mining Extensions), un linguaggio di query standard del settore orientato al data mining. e il linguaggio ASSL (Analysis Services Scripting Language), che consente di gestire gli oggetti di database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta anche un motore dei cubi locali che permette alle applicazioni in client senza connessione di esplorare dati multidimensionali archiviati localmente. Per ulteriori informazioni, vedere [requisiti di architettura Client per sviluppo Analysis Services](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 **Panoramica dell'architettura logica**  
 [Panoramica dell'architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Oggetti server**  
 [Oggetti server &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **Oggetti di database**  
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Oggetti Dimension**  
 [Gli oggetti dimensione &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Oggetti del cubo**  
 [Oggetti cubo &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sicurezza dall'accesso utente**  
 [Architettura di sicurezza di accesso utente](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'architettura Microsoft OLAP](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Architettura fisica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
