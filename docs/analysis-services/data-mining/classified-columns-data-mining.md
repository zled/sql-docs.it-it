---
title: Classificare le colonne (Data Mining) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 32b46928378a30daa9d998090d61b9a3ef19438c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="classified-columns-data-mining"></a>Colonne classificate (Data mining)
  Quando si definisce una colonna classificata, si crea una relazione tra la colonna corrente e un'altra colonna nella struttura di data mining. Nei dati nella colonna della struttura di data mining definita come colonna classificata sono contenute informazioni relative alle categorie in cui vengono descritti i valori in un'altra colonna nella struttura di data mining.  
  
 Si supponga, ad esempio, di disporre di due colonne con dati numerici: una colonna, [Yearly Purchases], contenente gli acquisti annuali totali per cliente per anno solare specifico e l'altra colonna, [Standard Deviations], contenente le deviazioni standard per tali valori. In questo caso, è possibile definire la colonna [Yearly Purchases] come classificata e questa relazione potrà essere usata dal modello nell'analisi.  
  
> [!NOTE]  
>  Gli algoritmi forniti in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non supportano l'utilizzo di colonne classificate. Questa funzionalità viene fornita per l'utilizzo nella creazione di algoritmi personalizzati.  
  
## <a name="defining-a-classified-column"></a>Definizione di una colonna classificata  
 Il tipo di dati di una colonna classificata deve essere **Long** o **Double**.  
  
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
 [Tipi di contenuto &#40;Data mining&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Strutture di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Tipi di dati &#40;Data mining&#41;](../../analysis-services/data-mining/data-types-data-mining.md)  
  
  
