---
title: Definire gruppi di membri | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 70a192c25c9271824bcf1ea74c7de68ce0b44651
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-properties---define-member-groups"></a>Attributo di proprietà: definire i gruppi di membri
  Se un attributo include un numero elevato di membri, è possibile scegliere di raggruppare tali membri in bucket, riducendo il numero di membri visualizzati dagli utenti durante la ricerca dei dati in una gerarchia. È inoltre possibile determinare il numero di bucket in cui sono raggruppati i membri e impostare uno schema di denominazione per i bucket. Per altre informazioni, vedere [Raggruppare membri di attributo &#40;discretizzazione&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
 I membri vengono raggruppati impostando la proprietà **DiscretizationMethod**, accessibile tramite la finestra **Proprietà** di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Durante la creazione di gruppi di membri, le modifiche apportate non sono disponibili per gli utenti fino a quando non è stata elaborata la dimensione. Per altre informazioni, vedere [Elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Per creare gruppi di membri  
  
1.  Aprire la dimensione che si desidera utilizzare. Per impostazione predefinita, verrà visualizzata la scheda **Struttura dimensione** .  
  
2.  In **Attributi**fare clic con il pulsante destro del mouse sull'attributo di cui si vuole raggruppare i membri e quindi scegliere **Proprietà**.  
  
3.  Selezionare un metodo di raggruppamento dei membri nell'elenco a discesa accanto alla proprietà **DiscretizationMethod**. Per altre informazioni sulle impostazioni della proprietà **DiscretizationMethod**, vedere [Raggruppare membri di attributo &#40;discretizzazione&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
  
