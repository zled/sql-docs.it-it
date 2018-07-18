---
title: Classificare le colonne (Data Mining) | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b014f82376b15d9d29834103d8827bf31231ef90
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019948"
---
# <a name="classified-columns-data-mining"></a>Colonne classificate (Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
 [Contenuto di Data Mining tipi & #40; & #41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Strutture di data mining & #40; Analysis Services - Data Mining & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Tipi di dati & #40; Data Mining & #41;](../../analysis-services/data-mining/data-types-data-mining.md)  
  
  
