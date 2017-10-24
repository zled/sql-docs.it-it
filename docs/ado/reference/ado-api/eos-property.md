---
title: "Proprietà di fine del flusso | Documenti Microsoft"
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
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c29c72e9cd88ff5672b90aeab5da97c7742f5b30
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="eos-property"></a>Proprietà di fine del flusso
Indica se la posizione corrente è alla fine del [flusso](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **booleano** valore che indica se la posizione corrente è alla fine del flusso. **Fine del flusso** restituisce **True** se esistono più byte nel flusso; restituisce **False** se sono presenti più i byte dopo la posizione corrente.  
  
 Per impostare la fine della posizione di flusso, utilizzare il [SetEOS](../../../ado/reference/ado-api/seteos-method.md) metodo. Per determinare la posizione corrente, utilizzare il [posizione](../../../ado/reference/ado-api/position-property-ado.md) proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Fine del flusso e proprietà di LineSeparator ed esempio di metodo SkipLine (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

