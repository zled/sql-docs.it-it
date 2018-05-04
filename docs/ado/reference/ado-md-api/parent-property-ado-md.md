---
title: Proprietà (ADO MD) padre | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4342e5f2b77b88b2c0050152306b660ea7d5cacf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parent-property-ado-md"></a>Proprietà padre (ADO MD)
Indica il membro padre dell'oggetto corrente [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) in una gerarchia.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) oggetto ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Un membro al livello superiore di una gerarchia (radice) non ha elementi padre. Questa proprietà è supportata solo in **membro** oggetti appartenenti a un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) oggetto. Si verifica un errore quando questa proprietà viene fatto riferimento dal **membro** oggetti appartenenti a un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md) oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Children (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
