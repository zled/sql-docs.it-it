---
title: Elemento CurrentStorageMode (ASSL) | Documenti Microsoft
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
- CurrentStorageMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentStorageMode
helpviewer_keywords:
- CurrentStorageMode element
ms.assetid: 050c21e4-368b-4ff0-b0c5-349f93fe9747
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cce7bfd399c0c986a79e919c6227ee604e9ff470
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067473"
---
# <a name="currentstoragemode-element-assl"></a>Elemento CurrentStorageMode (ASSL)
  Determina la modalità di archiviazione corrente per l'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension> <!-- or Partition -->  
   <CurrentStorageMode>...</CurrentStorageMode>  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ROLAP*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una volta o mai.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimensione](../objects/dimension-element-assl.md), [partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento `CurrentStorageMode` indica la modalità di archiviazione attualmente utilizzata per scopi di memorizzazione nella cache attiva e si applica a tutti gli attributi dell'elemento padre.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*MOLAP*|L'elemento padre utilizza l'archiviazione OLAP multidimensionale (MOLAP).|  
|*ROLAP*|L'elemento padre utilizza l'archiviazione OLAP relazionale (ROLAP).|  
|*HOLAP*|L'elemento padre utilizza l'archiviazione OLAP ibrido (HOLAP). **Nota:** questo valore è valido solo per [partizione](../objects/partition-element-assl.md) gli elementi padre.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `CurrentStorageMode` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.StorageMode>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  