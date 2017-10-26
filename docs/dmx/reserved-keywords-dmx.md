---
title: Parole chiave (DMX) riservate | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], reserved keywords
- reserved words [DMX]
- DMX [Analysis Services], reserved keywords
ms.assetid: d74871b0-d33f-4ee0-b1c7-384817c45e66
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f394df445ba40050a55c0b1f6a5c714b1ec4d298
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="reserved-keywords-dmx"></a>Parole chiave riservate (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] riserva determinate parole chiave per l'utilizzo esclusivo. Tali parole chiave non possono essere utilizzate liberamente nelle istruzioni DMX (Data Mining Extensions), ma solo nelle posizioni definite da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nelle informazioni di riferimento al linguaggio DMX. Queste parole chiave DMX con restrizioni includono i membri seguenti:  
  
-   Tutte le istruzioni di definizione dati elencate nell'argomento [istruzioni di definizione dati DMX](../dmx/dmx-statements-data-definition.md).  
  
-   Tutti i dati elencate nell'argomento, le funzioni di query di data mining [riferimento alle funzioni DMX](../dmx/data-mining-extensions-dmx-function-reference.md).  
  
-   Tutti gli operatori elencati nell'argomento [riferimento agli operatori DMX](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
-   Le parole chiave definite nel linguaggio di query MDX (Multidimensional Expressions) sono incluse come parte di un'istruzione DMX.  
  
-   Le parole chiave definite nella specifica OLE DB for Data Mining sono incluse come parte di un'istruzione DMX.  
  
 Quando si assegnano nomi agli oggetti di un database, è consigliabile utilizzare una convenzione di denominazione che eviti l'utilizzo delle parole chiave riservate.  
  
 Se il database contiene nomi che corrispondono a parole chiave riservate, sarà necessario utilizzare identificatori delimitati per fare riferimento a tali oggetti. Per ulteriori informazioni, vedere [DMX gli identificatori &#40; &#41;](../dmx/identifiers-dmx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Informazioni sull'istruzione Select di DMX](../dmx/understanding-the-dmx-select-statement.md)  
  
  

