---
title: Aggiornamento di celle (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
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
manager: mblythe
ms.openlocfilehash: f2a4a8976602080f28f736814783397bc6611e64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166946"
---
# <a name="updating-cells-xmla"></a>Aggiornamento di celle (XMLA)
  È possibile usare il [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) comandi per modificare il valore di uno o più celle in un cubo abilitato per il writeback del cubo. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Archivia le informazioni aggiornate in una tabella writeback separata per ogni partizione che contiene le celle da aggiornare.  
  
> [!NOTE]  
>  Il comando `UpdateCells` non supporta le allocazioni durante il writeback del cubo. Per utilizzare l'allocazione del writeback, è consigliabile usare la [istruzione](../xmla/xml-elements-commands/statement-element-xmla.md) comandi per inviare un'istruzione UPDATE di MDX (Multidimensional Expressions). Per altre informazioni, vedere [istruzione UPDATE CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Specifica di celle  
 Il [cella](../xmla/xml-elements-properties/cell-element-xmla.md) proprietà del `UpdateCells` comando contiene le celle da aggiornare. Per identificare ogni cella nella proprietà `Cell`, utilizzare i numero ordinale della cella specifica. Concettualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numeri di celle in un cubo come se quest'ultimo fosse una *p*-matrice dimensionale, in cui *p* è il numero di assi. Le celle sono indirizzate in ordine di riga. Nell'illustrazione seguente viene illustrata la formula per calcolare il numero ordinale di una cella.  
  
 ![Formula per calcolare la posizione ordinale della cella](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "Formula per calcolare la posizione ordinale della cella")  
  
 Dopo avere ottenuto un numero ordinale della cella, è possibile indicare il valore desiderato della cella nella [valore](../xmla/xml-elements-properties/value-element-xmla.md) proprietà del [cella](../xmla/xml-elements-properties/cell-element-xmla.md) proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornare l'elemento &#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
