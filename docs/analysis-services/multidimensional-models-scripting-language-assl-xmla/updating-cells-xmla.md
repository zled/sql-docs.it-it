---
title: Aggiornamento di celle (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1e886925621378aa5d01cc77a74edf0e1ea246cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="updating-cells-xmla"></a>Aggiornamento di celle (XMLA)
  È possibile utilizzare il [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) comando per modificare il valore di uno o più celle in un cubo abilitato per il writeback del cubo. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Archivia le informazioni aggiornate in una tabella writeback separata per ogni partizione che contiene le celle da aggiornare.  
  
> [!NOTE]  
>  Il **UpdateCells** comando non supporta le allocazioni durante il writeback del cubo. Per utilizzare l'allocazione del writeback, è consigliabile utilizzare il [istruzione](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando per inviare un'istruzione UPDATE di MDX (Multidimensional Expressions). Per altre informazioni, vedere [istruzione UPDATE CUBE &#40;MDX&#41;](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Specifica di celle  
 Il [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) proprietà del **UpdateCells** comando contiene le celle da aggiornare. Identificare ogni cella nel **cella** proprietà utilizzando un numero ordinale della cella. Concettualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numeri celle in un cubo come se fosse il cubo un *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga. Nell'illustrazione seguente viene illustrata la formula per calcolare il numero ordinale di una cella.  
  
 ![Formula per calcolare la posizione ordinale della cella](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "Formula per calcolare la posizione ordinale della cella")  
  
 Quando si conosce numero ordinale di una cella, è possibile indicare il valore desiderato della cella di [valore](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) proprietà del [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Update & #40; XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
