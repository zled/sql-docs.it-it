---
title: "Lo stato delle proprietà (ADO MD) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1886dae43bdb764a67fa5e44b1e8fe9744c0cb5f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="state-property-ado-md"></a>Proprietà state (ADO MD)
Indica lo stato corrente del set di celle.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **lungo** intero che indica la condizione corrente del [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto ed è di sola lettura. I seguenti valori validi sono: **adStateClosed** (0) e **adStateOpen** (1).  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) i nomi delle costanti, è necessario disporre della libreria dei tipi ADO a cui fa riferimento nel progetto. Vedere [utilizzo di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) per ulteriori informazioni.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Close (metodo) (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Metodo Open (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
