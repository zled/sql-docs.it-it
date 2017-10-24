---
title: "Nome proprietà (ADO MD) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d898b2e478b9a5dfccb431d0d29088c9e8d9286
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="name-property-ado-md"></a>Proprietà Name (ADO MD)
Indica il nome di un oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **stringa** ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile recuperare il **nome** proprietà di un oggetto da un riferimento ordinale, dopo il quale è possibile fare riferimento all'oggetto direttamente per nome. Ad esempio, se `cdf.CubeDefs(0).Name` restituisce "Nomecomputer Video Store", è possibile fare riferimento a questo [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) come `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto asse (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Oggetto del catalogo (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Oggetto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Oggetto dimensione (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Oggetto Hierarchy (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Oggetto di livello (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Oggetto membro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di catalogo (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Proprietà Caption (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Proprietà Description (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [Proprietà UniqueName (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)

