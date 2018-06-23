---
title: Oggetti (Analysis Services - dati multidimensionali) di database | Documenti Microsoft
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
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4f92a99eef0513a03d4158c4a30c8cc20210a516
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157605"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>Oggetti di database (Analysis Services - Dati multidimensionali)
  Un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza contiene oggetti di database e gli assembly per l'utilizzo con elaborazione analitica online (OLAP) e il data mining.  
  
-   I database contengono oggetti OLAP e di data mining, ad esempio origini dei dati, viste origine dati, cubi, misure, gruppi di misure, dimensioni, attributi, gerarchie, strutture di data mining, modelli di data mining e ruoli.  
  
-   Gli assembly contengono le funzioni definite dall'utente che estendono la funzionalità delle funzioni intrinseche disponibili nei linguaggi MDX (Multidimensional Expressions) e DMX (Data Mining Extensions).  
  
 L'oggetto <xref:Microsoft.AnalysisServices.Database> è il contenitore per tutti gli oggetti dati necessari per un progetto Business Intelligence, ad esempio cubi, dimensioni e strutture di data mining OLAP, e per gli oggetti di supporto, ad esempio <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account> e <xref:Microsoft.AnalysisServices.Role>.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Database> fornisce l'accesso agli oggetti e agli attributi che includono quanto segue:  
  
-   Tutti i cubi a cui è possibile accedere, sotto forma di raccolta.  
  
-   Tutte le dimensioni a cui è possibile accedere, sotto forma di raccolta.  
  
-   Tutte le strutture di data mining a cui è possibile accedere, sotto forma di raccolta.  
  
-   Tutte le origini dati e le viste origine dati, sotto forma di due raccolte.  
  
-   Tutti i ruoli e le autorizzazioni per il database, sotto forma di due raccolte.  
  
-   I valori delle regole di confronto per il database.  
  
-   Le dimensioni stimate del database.  
  
-   Il valore della lingua del database.  
  
-   L'impostazione di visibilità per il database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti vengono descritti gli oggetti condivisi sia dalle caratteristiche OLAP che da quelle di data mining in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Origini dati nei modelli multidimensionali](../data-sources-in-multidimensional-models.md)|Descrive un'origine dei dati in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Viste origine dati nei modelli multidimensionali](../data-source-views-in-multidimensional-models.md)|Descrive un modello di dati logico basato su una o più origini dei dati in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Cubi nei modelli multidimensionali](../cubes-in-multidimensional-models.md)|Descrive i cubi e gli oggetti dei cubi, inclusi gruppi di misure, misure, relazioni tra l'utilizzo delle dimensioni, calcoli, indicatori di prestazioni chiavi, azioni, traduzioni, partizioni e prospettive.|  
|[Le dimensioni &#40;Analysis Services - dati multidimensionali&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Descrive le dimensioni e gli oggetti delle dimensioni, inclusi attributi, relazioni tra attributi, gerarchie, livelli e membri.|  
|[Strutture di data mining &#40;Analysis Services - Data Mining&#41;](../../data-mining/mining-structures-analysis-services-data-mining.md)|Descrive le strutture e gli oggetti di data mining, inclusi i modelli di data mining.|  
|[I ruoli di sicurezza &#40;Analysis Services - dati multidimensionali&#41;](security-roles-analysis-services-multidimensional-data.md)|Descrive un ruolo, ovvero il meccanismo di sicurezza utilizzato per controllare l'accesso agli oggetti in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Gestione di assembly di modello multidimensionale](../multidimensional-model-assemblies-management.md)|Descrive un assembly, ovvero una raccolta di funzioni definite dall'utente utilizzate per estendere i linguaggi MDX e DMX in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati supportate &#40;multidimensionale di SSAS&#41;](../supported-data-sources-ssas-multidimensional.md)   
 [Soluzioni di modelli multidimensionali &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md)   
 [Soluzioni di Data Mining](../../data-mining/data-mining-solutions.md)  
  
  