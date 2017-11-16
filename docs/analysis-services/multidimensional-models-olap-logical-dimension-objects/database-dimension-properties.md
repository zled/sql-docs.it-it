---
title: "Proprietà delle dimensioni del database | Documenti Microsoft"
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eb55d98319fcfe4b09e489cf8b9e21bf9932c408
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimension-properties"></a>Proprietà delle dimensioni del database
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le caratteristiche di una dimensione sono definite dai metadati per la dimensione, in base alle impostazioni di diverse proprietà della dimensione e gli attributi o le gerarchie contenute nella dimensione. Nella tabella seguente vengono descritte le proprietà delle dimensioni in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**AttributeAllMemberName**|Specifica il nome del membro Totale per gli attributi in una dimensione.|  
|**Confronto**|Determina le regole di confronto utilizzate dalla dimensione.|  
|**CurrentStorageMode**|Contiene la modalità di archiviazione corrente per la dimensione.|  
|**Valore DependsOnDimension**|Contiene l'ID di un'altra dimensione da cui dipende la dimensione, se presente.|  
|**Description**|Contiene la descrizione della dimensione.|  
|**ErrorConfiguration**|Impostazioni configurabili per la gestione degli errori, relative alla gestione di chiavi duplicate, chiavi sconosciute, limiti di errore, azione da intraprendere in caso di rilevamento di un errore, file di log degli errori e gestione della chiave Null.|  
|**ID**|Contiene l'identificatore univoco (ID) della dimensione.|  
|**Lingua**|Specifica la lingua predefinita per la dimensione.|  
|**MdxMissingMemberMode**|Determina la modalità di gestione dei membri mancanti per le istruzioni MDX (Multidimensional Expressions).|  
|**MiningModelID**|Contiene l'ID del modello di data mining a cui è associata la dimensione di data mining. Questa proprietà è applicabile solo se la dimensione è una dimensione di un modello di data mining.|  
|**Nome**|Specifica il nome della dimensione.|  
|**ProactiveCaching**|Definisce le impostazioni di memorizzazione nella cache attiva per la dimensione.|  
|**ProcessingGroup**|Specifica il gruppo di elaborazione. I valori sono ByAttribute o ByTable. Valore predefinito è **ByAttribute**.|  
|**ProcessingMode**|Indica se in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] l'indicizzazione e l'aggregazione devono venire eseguite durante o dopo l'elaborazione.|  
|**ProcessingPriority**|Determina la priorità di elaborazione della dimensione durante le operazioni in background, ad esempio clustering, indicizzazione o aggregazione lenta.|  
|**Origine**|Identifica la vista origine dati a cui è associata la dimensione.|  
|**StorageMode**|Determina la modalità di archiviazione per la dimensione.|  
|**Tipo**|Specifica il tipo della dimensione.|  
|**UnknownMember**|Indica se il membro sconosciuto è visibile.|  
|**UnknownMemberName**|Specifica la didascalia, nella lingua predefinita della dimensione, per il membro sconosciuto della dimensione.|  
|**WriteEnabled**|Indica se i writeback della dimensione sono disponibili, in base alle autorizzazioni di sicurezza.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'impostazione dei valori per le proprietà ErrorConfiguration e UnknownMember quando si lavora con i valori null e altri problemi di integrità dei dati, vedere [la gestione di problemi di integrità dei dati in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Gerarchie definite dall'utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Relazioni tra dimensioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Dimensioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  

