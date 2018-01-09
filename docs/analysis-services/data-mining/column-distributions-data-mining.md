---
title: Distribuzioni delle colonne (Data Mining) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
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
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 98ba6df252c33f55aa5081ed6714c316c0ad1c4b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="column-distributions-data-mining"></a>Distribuzioni delle colonne (Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile definire le distribuzioni di colonna in una struttura di data mining per determinare come gli algoritmi elaborano i dati in tali colonne quando si creano modelli di data mining. Per alcuni algoritmi è utile definire la distribuzione dei dati nelle colonne continue prima di elaborare il modello, se è noto che tali colonne contengono valori con distribuzioni comuni. Se non si definiscono le distribuzioni, i modelli di data mining risultanti possono produrre stime meno accurate, perché gli algoritmi dispongono di meno informazioni per l'interpretazione dei dati.  
  
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
  
  
