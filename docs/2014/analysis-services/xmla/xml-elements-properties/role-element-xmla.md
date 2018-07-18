---
title: Elemento Role (XMLA) | Microsoft Docs
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
ms.assetid: 2b851ad5-cc46-4a2e-8873-d8556faca809
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4a2c2495a29481be7463e347677c1f74ffd23860
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265224"
---
# <a name="role-element--xmla"></a>Elemento Role (XMLA)
  Identifica un'estremità di una relazione uno-a-molti per essere usato dall'elemento padre [RelationshipEnd](../../scripting/data-type/relationshipend-data-type-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEnd  
   ...  
   <Role>...</Role>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEnd](../../scripting/data-type/relationshipend-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
  
