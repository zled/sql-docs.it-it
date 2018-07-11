---
title: Colonne (Data Mining) classificate | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 403ab773012d9e9370959bd7094db51f9785e8d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210341"
---
# <a name="classified-columns-data-mining"></a>Colonne classificate (Data mining)
  Quando si definisce una colonna classificata, si crea una relazione tra la colonna corrente e un'altra colonna nella struttura di data mining. Nei dati nella colonna della struttura di data mining definita come colonna classificata sono contenute informazioni relative alle categorie in cui vengono descritti i valori in un'altra colonna nella struttura di data mining.  
  
 Si supponga, ad esempio, di disporre di due colonne con dati numerici: una colonna, [Yearly Purchases], contenente gli acquisti annuali totali per cliente per anno solare specifico e l'altra colonna, [Standard Deviations], contenente le deviazioni standard per tali valori. In questo caso, è possibile definire la colonna [Yearly Purchases] come classificata e questa relazione potrà essere usata dal modello nell'analisi.  
  
> [!NOTE]  
>  Gli algoritmi forniti in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non supportano l'utilizzo di colonne classificate. Questa funzionalità viene fornita per l'utilizzo nella creazione di algoritmi personalizzati.  
  
## <a name="defining-a-classified-column"></a>Definizione di una colonna classificata  
 Il tipo di dati di una colonna classificata deve essere `Long` o `Double`.  
  
 Nell'elenco seguente vengono descritti i tipi di contenuto supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per le colonne classificate.  
  
 **PROBABILITY**  
 Il valore della colonna indica la probabilità del valore associato ed è un numero compreso tra 0 e 1.  
  
 **VARIANCE**  
 Il valore della colonna indica la varianza del valore associato.  
  
 **STDEV**  
 Il valore della colonna indica la deviazione standard del valore associato.  
  
 **PROBABILITY_VARIANCE**  
 Il valore della colonna indica la varianza della probabilità per il valore associato.  
  
 **PROBABILITY_STDEV**  
 Il valore della colonna indica la deviazione standard della probabilità per il valore associato.  
  
 **SUPPORT**  
 Il valore della colonna indica il peso o fattore di replica del case del valore associato.  
  
## <a name="see-also"></a>Vedere anche  
 [I tipi di contenuto &#40;Data Mining&#41;](content-types-data-mining.md)   
 [Strutture di data mining &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Tipi di dati &#40;Data Mining&#41;](data-types-data-mining.md)  
  
  
