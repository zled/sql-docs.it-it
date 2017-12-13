---
title: Escludere una colonna da un modello di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
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
ms.topic: article
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 13d32dde3f56772b3f8ee40bcc1e231c32f8bcef
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="exclude-a-column-from-a-mining-model"></a>Escludere una colonna da un modello di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Quando si crea un nuovo modello di data mining, si desidera utilizzare tutte le colonne presenti nella struttura di data mining su cui è basato il modello. È ad esempio probabile che sia stata aggiunta una colonna nome cliente per il drill-through, ma che non si desideri utilizzarla per la modellazione. In alternativa, è possibile decidere di creare più copie di una colonna con discretizzazioni diverse e utilizzare solo una delle copie in ogni modello e ignorare il resto. È anche possibile aggiungere in modo selettivo le colonne di input in molti modelli diversi per capire come la variabile aggiunta influisce sulla colonna di output.  
  
 Non è necessario creare una nuova struttura di data mining per ogni combinazione di colonne; è semplicemente possibile contrassegnare una colonna come non utilizzata in un determinato modello.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Per escludere una colonna da un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare la cella corrispondente alla colonna che si desidera escludere, nel modello di data mining appropriato.  
  
2.  Selezionare **Ignora** nell'elenco a discesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
