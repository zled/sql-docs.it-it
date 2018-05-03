---
title: Sezionare elemento (ASSL) | Documenti Microsoft
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
- Slice Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Slice
helpviewer_keywords:
- Slice element
ms.assetid: 2c8c4107-c641-4724-bfa5-0c47e0ec8888
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5d1a7ed876c50e6da984314cdd9f58bb778f5018
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="slice-element-assl"></a>Elemento Slice (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene un'espressione MDX (Multidimensional Expressions) che definisce la sezione contenuta in una partizione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Partition>  
      ...  
   <Slice>...</Slice>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Partizione](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **sezione** elemento contiene un'espressione di tupla MDX o un'espressione set che identifica la parte del cubo per cui la partizione archivia informazioni. L'espressione MDX è simile al [StrToSet](../../../mdx/strtoset-mdx.md) funzione MDX con la parola chiave CONSTRAINED, in quanto l'espressione non può includere funzioni MDX o definite dall'utente.  
  
 L'elemento che corrisponde all'elemento padre **sezione** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
