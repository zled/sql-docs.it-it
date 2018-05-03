---
title: Le proprietà del modello di data mining | Documenti Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b29794e3c41f218f1bd117fd68ad5a978066b150
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mining-model-properties"></a>Proprietà dei modelli di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  I modelli di data mining dispongono dei tipi seguenti di proprietà:  
  
-   Proprietà ereditate dalla struttura di data mining tramite cui vengono definiti il tipo di dati e il tipo di contenuto dei dati utilizzati dal modello  
  
-   Proprietà correlate all'algoritmo utilizzato per creare il modello di data mining, inclusi eventuali parametri del cliente  
  
-   Proprietà che definiscono un filtro sul modello utilizzato per eseguire il training del modello.  
  
 Le proprietà di un modello di data mining vengono definite inizialmente quando si crea il modello; è tuttavia possibile modificare la maggior parte delle proprietà in un secondo momento, inclusi i parametri dell'algoritmo, i filtri e le proprietà di utilizzo delle colonne. Tramite la scheda **Modelli di data mining** di Progettazione modelli di data mining, AMO o XMLA è possibile modificare le proprietà dei modelli di data mining.  
  
 Quando si modifica qualsiasi proprietà di un modello, è necessario rielaborare quest'ultimo in modo che vi vengano implementate le modifiche. La rielaborazione è necessaria anche se la modifica riguarda solo i metadati, ad esempio l'aggiunta di un alias o di una descrizione di colonna.  
  
## <a name="properties-of-models"></a>Proprietà dei modelli  
 Nella tabella seguente vengono descritte le proprietà specifiche dei modelli di data mining. Esistono inoltre proprietà che è possibile impostare su singole colonne di data mining  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Algoritmo**|Imposta il tipo di algoritmo per il modello di data mining.|  
|**AlgorithmParameters**|Imposta i valori dei parametri di algoritmo disponibili per ogni tipo di algoritmo.|  
|**Filter**|Imposta un filtro che viene applicato ai dati utilizzati per il training e il test del modello di data mining. La definizione del filtro è archiviata con il modello e può essere utilizzata facoltativamente quando si creano query di stima oppure per testare l'accuratezza del modello.<br /><br /> Il filtro del modello non è facoltativo quando si esegue il training del modello.|  
|**Nome**|Imposta il nome del modello di data mining.|  
|**AllowDrillThrough**|Specifica se nel modello di data mining è consentito il drill-through.|  
  
## <a name="properties-of-model-columns"></a>Proprietà delle colonne del modello  
 È possibile impostare le proprietà specifiche del data mining elencate di seguito per ogni colonna di un modello di data mining. Le proprietà possono essere impostate su un valore diverso per ogni modello di data mining di una struttura di data mining.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Description**|Viene descritto lo scopo della colonna di data mining.|  
|**Nome**|Imposta il nome della colonna del modello di data mining. È possibile digitare un nuovo nome per fornire un alias per la colonna del modello di data mining.|  
|**ModelingFlags**|Imposta i flag specifici dell'algoritmo per la colonna.|  
|**SourceColumnID**|Indica il nome della colonna della struttura di data mining su cui si basa la colonna del modello.<br /><br /> Questa proprietà è di sola lettura.|  
|**Utilizzo**|Imposta la modalità di utilizzo della colonna nel modello di data mining.|  
  
## <a name="see-also"></a>Vedere anche  
 [Colonne del modello di data mining](../../analysis-services/data-mining/mining-model-columns.md)   
 [Strutture di data mining & #40; Analysis Services - Data Mining & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Procedure dettagliate e attività di modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Modificare le proprietà di un modello di Data Mining](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)   
 [Strumenti di Data Mining](../../analysis-services/data-mining/data-mining-tools.md)   
 [Creare una struttura di Data Mining relazionale](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [Creare un Alias per una colonna del modello](../../analysis-services/data-mining/create-an-alias-for-a-model-column.md)  
  
  
