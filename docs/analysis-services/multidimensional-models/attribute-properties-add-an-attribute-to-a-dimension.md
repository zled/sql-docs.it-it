---
title: Aggiungere un attributo a una dimensione | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e512d61e1417bd5ad794f48289f537777a34f307
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="attribute-properties---add-an--attribute-to-a-dimension"></a>Attributo di proprietà - aggiungere un attributo a una dimensione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è possibile aggiungere un attributo a una dimensione automaticamente o manualmente.  
  
 Per creare un attributo automaticamente, nella scheda **Struttura dimensione** di Progettazione dimensioni, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], selezionare la colonna di cui si vuole eseguire il mapping a un attributo e quindi trascinare tale colonna nel riquadro **Attributi** dal riquadro **Vista origine dati** . Verrà creato un attributo di cui viene eseguito il mapping alla colonna al quale verrà assegnato lo stesso nome della colonna. Se esiste già un attributo con lo stesso nome, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aggiungerà al nome un suffisso composto da un numero ordinale, a partire da "1" per il primo nome duplicato.  
  
 Per creare un attributo manualmente, attivare la visualizzazione griglia nel riquadro **Attributi**. Nella colonna nome dell'ultima riga nella griglia, fare clic su di  **\<nuovo attributo >** elemento. Digitare un nome per il nuovo attributo. Verrà creato un attributo di cui viene eseguito il mapping a una colonna con le impostazioni predefinite per tutte le proprietà. È possibile impostare il mapping nella finestra **Proprietà** di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] configurando la proprietà **KeyColumns** del nuovo attributo.  
  
 Per altre informazioni, vedere [Definire automaticamente un nuovo attributo](../../analysis-services/multidimensional-models/attribute-properties-define-a-new-attribute-automatically.md), [Associare un attributo a una colonna del nome](../../analysis-services/multidimensional-models/attribute-properties-bind-an-attribute-to-a-name-column.md)e [Modificare la proprietà KeyColumn di un attributo](../../analysis-services/multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)è possibile aggiungere un attributo a una dimensione automaticamente o manualmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
