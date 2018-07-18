---
title: Elaborare una struttura di Data Mining | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9cb977ace8ccd1856d9a08c8eeaa2cf698637e68
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017128"
---
# <a name="process-a-mining-structure"></a>Elaborare una struttura di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Per poter esplorare o utilizzare i modelli di data mining associati a una struttura di data mining, è necessario distribuire il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ed elaborare la struttura e i modelli di data mining. Inoltre, se si apporta una modifica alla struttura o ai modelli di data mining, verrà richiesto di eseguire di nuovo la distribuzione e l'elaborazione. L'elaborazione della struttura nella scheda **Struttura di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] comporta l'elaborazione di tutti i modelli associati.  
  
 È possibile elaborare una struttura di data mining utilizzando gli strumenti seguenti:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA: comando Process  
  
 Per informazioni sull'elaborazione di singoli modelli, vedere [Elaborare un modello di data mining](../../analysis-services/data-mining/process-a-mining-model.md).  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>Per elaborare una struttura di data mining e tutti i modelli di data mining associati utilizzando gli strumenti dati di SQL Server  
  
1.  Scegliere la voce di menu **Modello di data mining** , quindi **Elabora struttura di data mining e tutti i modelli** in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
     Se sono state apportate modifiche alla struttura, prima di elaborare i modelli verrà richiesto di ridistribuire la struttura. Scegliere **Sì**.  
  
2.  Fare clic su **eseguire** nel **struttura di Data Mining elaborazione - \<struttura >** la finestra di dialogo.  
  
     Verrà aperta la finestra di dialogo **Stato elaborazione** in cui vengono visualizzate informazioni sull'elaborazione dei modelli.  
  
3.  Fare clic su **Chiudi** nella finestra di dialogo **Stato elaborazione** dopo che l'elaborazione dei modelli è stata completata.  
  
4.  Fare clic su **Chiudi** nel **struttura di Data Mining elaborazione - \<struttura >** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Data mining struttura attività e procedure](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
