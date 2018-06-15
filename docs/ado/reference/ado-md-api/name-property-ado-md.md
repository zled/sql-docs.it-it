---
title: Nome proprietà (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07a54616c2dd16a3a1c7582cbfe36c31ca0bef09
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284720"
---
# <a name="name-property-ado-md"></a>Proprietà Name (ADO MD)
Indica il nome di un oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **stringa** ed è di sola lettura.  
  
## <a name="remarks"></a>Remarks  
 È possibile recuperare il **nome** proprietà di un oggetto da un riferimento ordinale, dopo il quale è possibile fare riferimento all'oggetto direttamente per nome. Ad esempio, se `cdf.CubeDefs(0).Name` restituisce "Nomecomputer Video Store", è possibile fare riferimento a questo [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) come `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Oggetto Catalog (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Oggetto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Oggetto Dimension (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Oggetto Hierarchy (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Oggetto Level (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Oggetto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di catalogo (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Proprietà Caption (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Proprietà Description (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [Proprietà UniqueName (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
