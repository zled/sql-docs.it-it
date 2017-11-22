---
title: Data Mining Extensions (DMX) di riferimento alle istruzioni | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], statements
- DMX [Analysis Services], statements
- statements [DMX], reference
- mining models [Analysis Services], training
- mining structures [DMX]
- mining models [Analysis Services], options
- mining structures [DMX], options
ms.assetid: 9cfa1db4-0f21-4fa3-8158-f94c48987e1b
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f8d5b41d7e484a89e5ccb1777e81b72bc9dba6b7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="data-mining-extensions-dmx-statements"></a>Istruzioni Data Mining Extensions (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Utilizzare i dati di data mining in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prevede le attività principali seguenti:  
  
-   Creazione di strutture e modelli di data mining  
  
-   Elaborazione di strutture e modelli di data mining  
  
-   Eliminazione di strutture e modelli di data mining  
  
-   Copia di modelli di data mining  
  
-   Visualizzazione di modelli di data mining  
  
-   Generazione di stime basate su modelli di data mining  
  
 È possibile utilizzare istruzioni DMX (Data Mining Extensions) per eseguire tali attività a livello di programmazione.  
  
 Creazione di strutture e modelli di data mining  
 Utilizzare il [DMX CREATE MINING STRUCTURE &#40; &#41;](../dmx/create-mining-structure-dmx.md) istruzione per aggiungere una nuova struttura di data mining a un database. È quindi possibile utilizzare il [DMX ALTER MINING STRUCTURE &#40; &#41;](../dmx/alter-mining-structure-dmx.md) istruzione per aggiungere modelli di data mining alla struttura di data mining.  
  
 Utilizzare il [DMX CREATE MINING MODEL &#40; &#41;](../dmx/create-mining-model-dmx.md) istruzione per creare una nuova struttura di data mining associato e modello di data mining.  
  
 Elaborazione di strutture e modelli di data mining  
 Utilizzare il [DMX INSERT INTO &#40; &#41;](../dmx/insert-into-dmx.md) istruzione per elaborare una struttura di data mining e un modello di data mining.  
  
 Eliminazione di strutture e modelli di data mining  
 Utilizzare il [DMX DELETE &#40; &#41;](../dmx/delete-dmx.md) istruzione per rimuovere tutti i dati con Training da un modello di data mining o una struttura di data mining. Utilizzare il [DMX create MINING STRUCTURE &#40; &#41;](../dmx/drop-mining-structure-dmx.md) o [DMX create MINING MODEL &#40; &#41;](../dmx/drop-mining-model-dmx.md) istruzioni per rimuovere completamente una struttura di data mining o un modello di data mining da un database.  
  
 Copia di modelli di data mining  
 Utilizzare il [DMX SELECT INTO &#40; &#41;](../dmx/select-into-dmx.md) istruzione per copiare la struttura di un modello di data mining esistente in un nuovo modello di data mining e per eseguire il training del nuovo modello con gli stessi dati.  
  
 Visualizzazione di modelli di data mining  
 Utilizzare il [DMX SELECT &#40; &#41;](../dmx/select-dmx.md) istruzione per visualizzare le informazioni che l'algoritmo di data mining calcola e archivia il modello di data mining durante il training del modello. Simile a quello con [!INCLUDE[tsql](../includes/tsql-md.md)], è possibile utilizzare numerose clausole con l'istruzione SELECT, per estenderne le funzionalità. Tali clausole includono [DISTINCT FROM \<modello >](../dmx/select-distinct-from-model-dmx.md), [FROM \<modello >. CASI](../dmx/select-from-model-cases-dmx.md), [FROM \<modello >. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md), [FROM \<modello >. CONTENUTO](../dmx/select-from-model-content-dmx.md) e [FROM \<modello >. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md).  
  
 Generazione di stime basate su modelli di data mining  
 Utilizzare il [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) clausola dell'istruzione SELECT per creare stime basate su un modello di data mining esistente.  
  
 È inoltre possibile importare ed esportare modelli utilizzando il [DMX importazione &#40; &#41;](../dmx/import-dmx.md) e [DMX esportazione &#40; &#41;](../dmx/export-dmx.md) istruzioni.  
  
 Queste attività rientrano in due categorie, istruzioni per la definizione dei dati e istruzioni per la manipolazione dei dati, descritte nella tabella seguente.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)|Fanno parte del linguaggio DDL (Data Definition Language). Consentono di definire un nuovo modello di data mining (incluso il training) o di eliminare un modello di data mining esistente da un database.|  
|[Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)|Fanno parte del linguaggio DML (Data Manipulation Language). Consentono di utilizzare modelli di data mining esistenti, eseguendo operazioni quali la visualizzazione di un modello o la creazione di stime.|  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  
