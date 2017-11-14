---
title: "Proprietà LineSeparator (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2be2e27fa93791647fd3e27945c3203cf1afe999
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="lineseparator-property-ado"></a>Proprietà LineSeparator (ADO)
Indica il carattere binario da utilizzare come separatore di riga nel testo [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) valore che indica il carattere separatore di riga utilizzato nel **flusso**. Il valore predefinito è **adCRLF**.  
  
## <a name="remarks"></a>Osservazioni  
 **LineSeparator** viene utilizzato per interpretare le righe durante la lettura del contenuto di un testo **flusso**. È possibile ignorare le righe con la [SkipLine](../../../ado/reference/ado-api/skipline-method.md) metodo.  
  
 **LineSeparator** viene utilizzato solo con testo **flusso** oggetti ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**). Questa proprietà viene ignorata se **tipo** è **adTypeBinary**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

