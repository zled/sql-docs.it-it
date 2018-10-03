---
title: Elemento Role (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 2b851ad5-cc46-4a2e-8873-d8556faca809
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 40bd787702243bcd85adb05eeb241330e08b63af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080411"
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
  
