---
title: Escludere una colonna da un modello di Data Mining | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 584303518d464508dd790f7c2488105f8c504baf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="exclude-a-column-from-a-mining-model"></a>Escludere una colonna da un modello di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Quando si crea un nuovo modello di data mining, potrebbe non essere necessario utilizzare tutte le colonne presenti nella struttura di data mining su cui il modello è basato. È ad esempio probabile che sia stata aggiunta una colonna nome cliente per il drill-through, ma che non si desideri utilizzarla per la modellazione. In alternativa, è possibile decidere di creare più copie di una colonna con discretizzazioni diverse e utilizzare solo una delle copie in ogni modello e ignorare il resto. È anche possibile aggiungere in modo selettivo le colonne di input in molti modelli diversi per capire come la variabile aggiunta influisce sulla colonna di output.  
  
 Non è necessario creare una nuova struttura di data mining per ogni combinazione di colonne; è semplicemente possibile contrassegnare una colonna come non utilizzata in un determinato modello.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Per escludere una colonna da un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare la cella corrispondente alla colonna che si desidera escludere, nel modello di data mining appropriato.  
  
2.  Selezionare **Ignora** nell'elenco a discesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività di modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
