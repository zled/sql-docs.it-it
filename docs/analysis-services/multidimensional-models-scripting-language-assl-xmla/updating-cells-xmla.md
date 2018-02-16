---
title: Aggiornamento di celle (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
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
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4349868e9e9656a5bbd735c9fa6c6741c95d6e57
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="updating-cells-xmla"></a>Aggiornamento di celle (XMLA)
  È possibile utilizzare il [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) comando per modificare il valore di uno o più celle in un cubo abilitato per il writeback del cubo. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Archivia le informazioni aggiornate in una tabella writeback separata per ogni partizione che contiene le celle da aggiornare.  
  
> [!NOTE]  
>  Il **UpdateCells** comando non supporta le allocazioni durante il writeback del cubo. Per utilizzare l'allocazione del writeback, è consigliabile utilizzare il [istruzione](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando per inviare un'istruzione UPDATE di MDX (Multidimensional Expressions). Per ulteriori informazioni, vedere [istruzione UPDATE CUBE &#40; MDX &#41; ](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Specifica di celle  
 Il [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) proprietà del **UpdateCells** comando contiene le celle da aggiornare. Identificare ogni cella nel **cella** proprietà utilizzando un numero ordinale della cella. Concettualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numeri celle in un cubo come se fosse il cubo un *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga. Nell'illustrazione seguente viene illustrata la formula per calcolare il numero ordinale di una cella.  
  
 ![Formula per calcolare la posizione ordinale della cella](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "Formula per calcolare la posizione ordinale della cella")  
  
 Quando si conosce numero ordinale di una cella, è possibile indicare il valore desiderato della cella di [valore](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) proprietà del [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Update &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
