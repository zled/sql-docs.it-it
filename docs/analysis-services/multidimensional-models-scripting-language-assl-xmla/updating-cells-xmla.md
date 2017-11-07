---
title: Aggiornamento di celle (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57edea50d67fa52de99f92b85b40bcd5caf307fb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="updating-cells-xmla"></a>Aggiornamento di celle (XMLA)
  È possibile utilizzare il [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) comando per modificare il valore di uno o più celle in un cubo abilitato per il writeback del cubo. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] archivia le informazioni aggiornate in una tabella writeback separata per ogni partizione che contiene le celle da aggiornare.  
  
> [!NOTE]  
>  Il **UpdateCells** comando non supporta le allocazioni durante il writeback del cubo. Per utilizzare l'allocazione del writeback, è consigliabile utilizzare il [istruzione](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando per inviare un'istruzione UPDATE di MDX (Multidimensional Expressions). Per ulteriori informazioni, vedere [istruzione UPDATE CUBE &#40; MDX &#41; ](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Specifica di celle  
 Il [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) proprietà del **UpdateCells** comando contiene le celle da aggiornare. Identificare ogni cella nel **cella** proprietà utilizzando un numero ordinale della cella. Concettualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numeri celle in un cubo come se fosse il cubo un *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga. Nell'illustrazione seguente viene illustrata la formula per calcolare il numero ordinale di una cella.  
  
 ![Formula per calcolare la posizione ordinale della cella](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "Formula per calcolare la posizione ordinale della cella")  
  
 Quando si conosce numero ordinale di una cella, è possibile indicare il valore desiderato della cella di [valore](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) proprietà del [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Update &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

