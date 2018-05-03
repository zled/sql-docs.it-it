---
title: Elemento MdxMissingMemberMode (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MdxMissingMemberMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MdxMissingMemberMode element
ms.assetid: aca6130b-5fb8-4fa1-af8b-8e1ef361926f
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2452957134b0c1118695e5a34565ca6053010eb8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdxmissingmembermode-element-assl"></a>Elemento MdxMissingMemberMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina la modalità di gestione dei membri mancanti per le istruzioni MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension>  
   ...  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Valore predefinito*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimensione](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Ignorare*|I membri mancanti vengono ignorati.|  
|*Errore*|Viene generato un errore se vengono rilevati membri mancanti.|  
|*Valore predefinito*|I membri mancanti vengono ignorati.|  
  
 L'elemento che corrisponde all'elemento padre **MdxMissingMemberMode** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni MDX & #40; MDX & #41; Riferimento](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
