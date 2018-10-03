---
title: Aggiornamento di celle (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3db80cd5573e115e3ec399470a7c2a249699e49f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061183"
---
# <a name="updating-cells-xmla"></a>Aggiornamento di celle (XMLA)
  È possibile usare la [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) comandi per modificare il valore di uno o più celle in un cubo abilitato per il writeback del cubo. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Archivia le informazioni aggiornate in una tabella writeback separata per ogni partizione che contiene le celle da aggiornare.  
  
> [!NOTE]  
>  Il comando `UpdateCells` non supporta le allocazioni durante il writeback del cubo. Per utilizzare l'allocazione del writeback, è consigliabile usare la [istruzione](../xmla/xml-elements-commands/statement-element-xmla.md) comando per inviare un'istruzione UPDATE di MDX (Multidimensional Expressions). Per altre informazioni, vedere [istruzione UPDATE CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Specifica di celle  
 Il [cella](../xmla/xml-elements-properties/cell-element-xmla.md) proprietà del `UpdateCells` comando contiene le celle da aggiornare. Per identificare ogni cella nella proprietà `Cell`, utilizzare i numero ordinale della cella specifica. Concettualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numeri di celle in un cubo come se quest'ultimo fosse una *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga. Nell'illustrazione seguente viene illustrata la formula per calcolare il numero ordinale di una cella.  
  
 ![Formula per calcolare la posizione ordinale della cella](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "Formula per calcolare la posizione ordinale della cella")  
  
 Dopo aver individuato un numero ordinale della cella, è possibile indicare il valore desiderato della cella i [valore](../xmla/xml-elements-properties/value-element-xmla.md) proprietà del [cella](../xmla/xml-elements-properties/cell-element-xmla.md) proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornare l'elemento &#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
