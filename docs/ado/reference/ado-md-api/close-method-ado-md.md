---
title: Close (metodo) (ADO MD) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords: Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 73cfa5ac30f9b7ac4e5e7d616b5e4f9eba4a2bef
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="close-method-ado-md"></a>Close (metodo) (ADO MD)
Chiude un set di celle aperto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzando il **chiudere** metodo per chiudere un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto rilascerà i dati associati, inclusi i dati in qualsiasi correlati [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md), o [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) oggetti. Chiusura di un **set di celle** senza rimuoverlo dalla memoria; è possibile modificare le impostazioni delle proprietà e aprirlo più tardi. Per eliminare completamente l'oggetto dalla memoria, impostare la variabile oggetto **nulla**.  
  
 Successivamente è possibile chiamare il [aprire](../../../ado/reference/ado-md-api/open-method-ado-md.md) metodo per riaprire il **set di celle** utilizzando lo stesso o in un'altra stringa di origine. Mentre il **set di celle** oggetto è chiuso, il recupero di tutte le proprietà o chiamare i metodi che fanno riferimento ai dati sottostanti o metadati viene generato un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto asse (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Oggetto Cell (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Oggetto membro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Open (metodo) (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Oggetto Position (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [Proprietà State (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
