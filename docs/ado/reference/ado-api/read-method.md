---
title: Metodo Read | Documenti Microsoft
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
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords: Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 740be677f54f8d4b5d30902a792b58d4681df888
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="read-method"></a>Read, metodo
Legge un numero specificato di byte da un file binario [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Parametri  
 *NumBytes*  
 Facoltativa. A **lungo** valore che specifica il numero di byte da leggere dal file o [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) valore **adReadAll**, ovvero l'impostazione predefinita.  
  
## <a name="return-value"></a>Valore restituito  
 Il **lettura** metodo legge un numero specificato di byte o tutto il flusso da un **flusso** specificato e restituisce i dati risultanti come un **Variant**.  
  
## <a name="remarks"></a>Osservazioni  
 Se *NumBytes* è maggiore del numero di byte nel **flusso**, vengono restituiti solo i byte rimanenti. I dati letti non possono essere riempiti per corrispondere alla lunghezza specificata da *NumBytes*. Se esistono byte rimanenti da leggere, viene restituito un variant con un valore null. **Lettura** non può essere usato per leggere le versioni precedenti.  
  
> [!NOTE]
>  *NumBytes* misura sempre byte. Per il testo **flusso** oggetti ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**), utilizzare [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo ReadText](../../../ado/reference/ado-api/readtext-method.md)
