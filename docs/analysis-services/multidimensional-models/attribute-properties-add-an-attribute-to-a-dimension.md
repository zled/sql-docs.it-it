---
title: Aggiungere un attributo a una dimensione | Documenti Microsoft
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
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d5f620f394ab70b0fea579875c23e7f0eb8716db
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="attribute-properties---add-an--attribute-to-a-dimension"></a>Attributo di proprietà - aggiungere un attributo a una dimensione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è possibile aggiungere un attributo a una dimensione automaticamente o manualmente.  
  
 Per creare un attributo automaticamente, nella scheda **Struttura dimensione** di Progettazione dimensioni, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], selezionare la colonna di cui si vuole eseguire il mapping a un attributo e quindi trascinare tale colonna nel riquadro **Attributi** dal riquadro **Vista origine dati** . Verrà creato un attributo di cui viene eseguito il mapping alla colonna al quale verrà assegnato lo stesso nome della colonna. Se esiste già un attributo con lo stesso nome, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aggiungerà al nome un suffisso composto da un numero ordinale, a partire da "1" per il primo nome duplicato.  
  
 Per creare un attributo manualmente, attivare la visualizzazione griglia nel riquadro **Attributi**. Nella colonna nome dell'ultima riga nella griglia, fare clic su di  **\<nuovo attributo >** elemento. Digitare un nome per il nuovo attributo. Verrà creato un attributo di cui viene eseguito il mapping a una colonna con le impostazioni predefinite per tutte le proprietà. È possibile impostare il mapping nella finestra **Proprietà** di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] configurando la proprietà **KeyColumns** del nuovo attributo.  
  
 Per altre informazioni, vedere [Definire automaticamente un nuovo attributo](../../analysis-services/multidimensional-models/attribute-properties-define-a-new-attribute-automatically.md), [Associare un attributo a una colonna del nome](../../analysis-services/multidimensional-models/attribute-properties-bind-an-attribute-to-a-name-column.md)e [Modificare la proprietà KeyColumn di un attributo](../../analysis-services/multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)è possibile aggiungere un attributo a una dimensione automaticamente o manualmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
