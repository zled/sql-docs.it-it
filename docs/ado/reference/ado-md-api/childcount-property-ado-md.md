---
title: "Proprietà ChildCount (ADO MD) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords: ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5976605c9bfb96a7dc53895eaa4cbc511fb321a2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="childcount-property-ado-md"></a>Proprietà ChildCount (ADO MD)
Indica il numero di membri per cui corrente [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) oggetto è l'elemento padre in una gerarchia.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **lungo** integer ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **ChildCount** proprietà per restituire una stima del numero di figli un **membro** ha. I figli effettivi di un **membro** possono essere restituiti dal [figli](../../../ado/reference/ado-md-api/children-property-ado-md.md) proprietà.  
  
 Per **membro** oggetti da un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md) dell'oggetto, il numero massimo restituito è 65536. Se il numero effettivo di elementi figlio supera i 65536, il valore restituito sarà ancora 65536. Pertanto, l'applicazione è necessario interpretare un **ChildCount** di 65536 come uguale o maggiore di 65536 figli.  
  
 Per **membro** oggetti da un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) oggetto, usare la raccolta di ADO [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà il **figli** insieme per determinare il numero esatto di figli. Determinare il numero esatto di elementi figlio potrebbe essere lenta se il numero di elementi figlio nella raccolta è di grandi dimensioni.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà di elementi figlio (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Proprietà Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Raccolta Members (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
