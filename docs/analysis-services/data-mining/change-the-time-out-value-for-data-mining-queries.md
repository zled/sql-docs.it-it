---
title: Modificare il valore di timeout di query di Data Mining | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6286a931c0e1ad27a99462853c3b8dfe6de36bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>Modificare il valore di timeout per le query di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Quando si compila un grafico di accuratezza o si esegue una query di stima, talvolta la generazione di tutti i dati necessari per la stima può richiedere una notevole quantità di tempo. Per impedire il timeout della query, è possibile modificare il valore che controlla l'intervallo di tempo durante il quale il server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attende il completamento di una query.  
  
 Il valore predefinito è 15; tuttavia, se i modelli sono complessi o l'origine dati è di grandi dimensioni, questo tempo potrebbe non essere sufficiente. Se necessario, è possibile aumentare notevolmente il valore in modo da assegnare una quantità di tempo sufficiente per l'elaborazione. Se ad esempio l'opzione **Timeout query** viene impostata su 600, l'esecuzione della query può continuare per un totale di 10 minuti.  
  
 Per altre informazioni sulle query di stima, vedere [Attività e procedure relative alle query di data mining](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Configurare il valore di timeout per le query di data mining  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel riquadro **Opzioni** espandere **Finestre di progettazione Business Intelligence**.  
  
3.  Fare clic sulla casella di testo **Timeout query** e digitare un valore per il numero di secondi.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività Query di data Mining](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Query di Data Mining](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
