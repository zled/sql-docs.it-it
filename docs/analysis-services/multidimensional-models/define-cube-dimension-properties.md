---
title: "Definire le proprietà di dimensione cubo | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6703e9f6c666a9a57be9d810811be0acb2a26127
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="define-cube-dimension-properties"></a>Definire le proprietà delle dimensioni del cubo
  Una dimensione del cubo è un'istanza della dimensione del database all'interno di un cubo. Una dimensione del database può essere utilizzata in più cubi e più dimensioni del cubo possono essere basate su una singola dimensione del database. Nella tabella seguente vengono descritte le proprietà della dimensione di un cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**AllMemberAggregationUsage**|Controlla il modo in cui vengono progettate le aggregazioni con Progettazione aggregazioni in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I possibili valori della proprietà sono i seguenti:<br /><br /> **Completo**: ogni aggregazione del cubo deve includere il membro Totale.<br /><br /> **Nessuno**: nessuna aggregazione del cubo può includere il membro Totale. Si tratta del valore predefinito.<br /><br /> **Senza restrizioni**: non esistono restrizioni in Progettazione aggregazioni.<br /><br /> **Valore predefinito**: stessa funzionalità di Senza restrizioni.|  
|**Description**|Fornisce un nome descrittivo per il livello.|  
|**DimensionID**|Contiene l'identificatore univoco (ID) della dimensione del database.|  
|**HierarchyUniqueNameStyle**|Determina il modo in cui vengono generati i nomi univoci delle gerarchie contenute all'interno della dimensione del cubo. I possibili valori della proprietà sono i seguenti:<br /><br /> **IncludeDimensionName**:<br />                    Il nome della dimensione fa parte del nome della gerarchia. Si tratta del valore predefinito.<br /><br /> **ExcludeDimensionName**:<br />                    Il nome della dimensione non fa parte del nome della gerarchia.|  
|**ID**|Contiene l'identificatore univoco della dimensione del cubo.|  
|**MemberUniqueNameStyle**|Determina il modo in cui vengono generati i nomi univoci dei membri delle gerarchie contenuti all'interno della dimensione del cubo. I possibili valori della proprietà sono i seguenti:<br /><br /> **Native**:<br />                      [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determina automaticamente i nomi univoci dei membri. Si tratta del valore predefinito.<br /><br /> **NamePath**: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] genera un nome composto costituito dal nome di ogni livello e dalla didascalia del membro.|  
|**Nome**|Contiene il nome descrittivo della dimensione del cubo. Per impostazione predefinita, il nome di una dimensione del cubo è uguale al nome della dimensione del database, a meno che non sia già stata definita un'altra dimensione del cubo con lo stesso nome.|  
|**Visible**|Determina se la dimensione del cubo è visibile. Il valore predefinito è **True**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
