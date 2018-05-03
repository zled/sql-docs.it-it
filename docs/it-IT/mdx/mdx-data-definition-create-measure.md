---
title: Istruzione CREATE MEASURE (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: f264ba96-cbbe-488b-8ac9-b3056a6e997b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c87b1b725489de8b163ab5a2a7d73794eddce9e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---create-measure"></a>Definizione dei dati MDX - creare misure
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di creare una misura in un modello tabulare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Table_Name*  
 Valore letterale stringa valido che fornisce il nome della tabella in cui verrà creata la misura.  
  
 *Measure_Name*  
 Valore letterale stringa valido che fornisce il nome di una misura.  
  
 *DAX_Expression*  
 Espressione DAX valida tramite cui viene restituito un singolo valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Il *Measure_Name* deve essere racchiuso tra parentesi quadre.  
  
 L'istruzione CREATE MEASURE può essere utilizzato solo all'interno di una definizione di script MDX. vedere [elemento MdxScript &#40;ASSL&#41;](../analysis-services/scripting/objects/mdxscript-element-assl.md).  
  
 È inoltre possibile definire un membro calcolato da usare in un'unica query. Per definire un membro calcolato limitato a una singola query, è possibile usare la clausola WITH nell'istruzione SELECT. Per ulteriori informazioni, vedere [compilazione di misure in MDX](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di definizione dei dati MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
