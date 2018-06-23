---
title: Tipo di dati TabularBinding (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TabularBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TabularBinding
helpviewer_keywords:
- TabularBinding data type
ms.assetid: 24587e34-20be-4693-81d8-038a6fc4e8ee
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 59206b9dd0d9f61ee0915076cd76fc36bdab9322
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065687"
---
# <a name="tabularbinding-data-type-assl"></a>Tipo di dati TabularBinding (ASSL)
  Definisce un tipo di dati derivato astratto che rappresenta un'associazione a un elemento tabulare, ad esempio una dimensione di un cubo o una tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TabularBinding>  
   <!-- The TabularBinding element has no child elements other than those inherited from Binding -->  
</TabularBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|[DSVTableBinding](tablebinding-data-type-assl.md), [QueryBinding](querybinding-data-type-assl.md), [TableBinding](tablebinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [tipo di dati Binding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e le associazioni &#40;multidimensionali SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TabularBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  