---
title: Distribuzioni delle colonne (Data Mining) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 96b2502e351f371163d5b748b432d381d237a8a9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="column-distributions-data-mining"></a>Distribuzioni delle colonne (Data mining)
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]è possibile definire le distribuzioni delle colonne di una struttura di data mining per determinare la modalità con cui gli algoritmi elaborano i dati di tali colonne durante la creazione dei modelli di data mining. Per alcuni algoritmi è utile definire la distribuzione dei dati nelle colonne continue prima di elaborare il modello, se è noto che tali colonne contengono valori con distribuzioni comuni. Se non si definiscono le distribuzioni, i modelli di data mining risultanti possono produrre stime meno accurate, perché gli algoritmi dispongono di meno informazioni per l'interpretazione dei dati.  
  
 Gli algoritmi disponibili in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supportano i tipi di distribuzioni seguenti:  
  
 **Normale**  
 I valori della colonna continua formano un istogramma con una distribuzione normale.  
  
 ![Istogramma con distribuzione normale](../../analysis-services/data-mining/media/normal-distribution.gif "istogramma con distribuzione normale")  
  
 **Logaritmica normale**  
 I valori della colonna continua formano un istogramma in cui l'estremità superiore della curva è allungata e l'estremità inferiore è asimmetrica.  
  
 ![Istogramma con distribuzione lognormale](../../analysis-services/data-mining/media/log-normal-distribution.gif "istogramma con distribuzione normale di log")  
  
 **Uniforme**  
 I valori della colonna continua formano una curva uniforme, in cui tutti i valori hanno la stessa probabilità.  
  
 ![Istogramma con distribuzione uniforme](../../analysis-services/data-mining/media/uniform-distribution.gif "istogramma con distribuzione uniforme")  
  
 Per altre informazioni sugli algoritmi forniti da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di contenuto &#40;Data mining&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Strutture di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Metodi di discretizzazione &#40; Data Mining &#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [DMX distribuzioni &#40; &#41;](../../dmx/distributions-dmx.md)   
 [Colonne della struttura di data mining](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  

