---
title: "Proprietà DrilledDown (ADO MD) | Documenti Microsoft"
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
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8dfa880e78bdeccf722723a7d05f2f0ca1938ed6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="drilleddown-property-ado-md"></a>Proprietà DrilledDown (ADO MD)
Indica se gli elementi figlio seguono immediatamente il [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) sull'asse.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **booleano** valore ed è di sola lettura. **DrilledDown** restituisce **True** se non esistono membri figlio del membro corrente sull'asse. **DrilledDown** restituisce **False** se il membro corrente ha uno o più membri figlio sull'asse.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **DrilledDown** proprietà per determinare se è presente almeno un elemento figlio di questo membro sull'asse immediatamente dopo questo membro. Queste informazioni sono utili quando si visualizza il membro.  
  
 Questa proprietà è supportata solo su [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) oggetti appartenenti a un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md) oggetto. Si verifica un errore quando questa proprietà viene fatto riferimento dal **membro** oggetti appartenenti a un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto membro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ParentSameAsPrev (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
