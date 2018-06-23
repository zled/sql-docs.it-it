---
title: Architettura logica (Analysis Services - dati multidimensionali) | Documenti Microsoft
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
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 468ad4b5f7456524b4d44552bd18cf80406bee07
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157021"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Architettura logica (Analysis Services - Dati multidimensionali)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza i componenti server e client per fornire l'elaborazione analitica online (OLAP) e funzionalità di data mining per applicazioni di business intelligence:  
  
-   Il componente server di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene implementato come un servizio di Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta più istanze nello stesso computer, con ogni istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementato come un'istanza separata del servizio Windows.  
  
-   I client comunicano con [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mediante lo standard pubblico XML for Analysis (XMLA), un protocollo basato su SOAP per l'esecuzione di comandi e la ricezione di risposte che viene esposto come un servizio Web. Tramite XMLA vengono inoltre offerti modelli a oggetti client a cui è possibile accedere usando un provider gestito, ad esempio ADOMD.NET, o un provider OLE DB nativo.  
  
-   I comandi di query possono essere eseguiti tramite i linguaggi seguenti: SQL, MDX (Multidimensional Expressions), un linguaggio di query standard del settore per l'analisi, o DMX (Data Mining Extensions), un linguaggio di query standard del settore orientato al data mining. e il linguaggio ASSL (Analysis Services Scripting Language), che consente di gestire gli oggetti di database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta anche un motore dei cubi locali che permette alle applicazioni in client senza connessione di esplorare dati multidimensionali archiviati localmente. Per altre informazioni, vedere [requisiti di architettura Client per sviluppo Analysis Services](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 **Panoramica dell'architettura logica**  
 [Panoramica dell'architettura logica &#40;Analysis Services - dati multidimensionali&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Oggetti server**  
 [Oggetti server &#40;Analysis Services - dati multidimensionali&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Oggetti di database**  
 [Gli oggetti di database &#40;Analysis Services - dati multidimensionali&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Oggetti Dimension**  
 [Oggetti dimensione &#40;Analysis Services - dati multidimensionali&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Oggetti del cubo**  
 [Oggetti cubo &#40;Analysis Services - dati multidimensionali&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sicurezza dall'accesso utente**  
 [Architettura di sicurezza di accesso utente](https://msdn.microsoft.com/library/bb522595(SQL.120).aspx)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'architettura Microsoft OLAP](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Architettura fisica &#40;Analysis Services - dati multidimensionali&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  