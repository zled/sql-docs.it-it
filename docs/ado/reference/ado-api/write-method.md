---
title: Write, metodo | Documenti Microsoft
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
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords: Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd956d5ff536105dc889e89d8f2d80f22db0e9c3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="write-method"></a>Write, metodo
Scrive dati binari in un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Parametri  
 *Buffer*  
 Oggetto **Variant** che contiene una matrice di byte da scrivere.  
  
## <a name="remarks"></a>Osservazioni  
 Byte specificati vengono scritti i **flusso** oggetto senza spazi intermedi tra ogni byte.  
  
 Corrente [posizione](../../../ado/reference/ado-api/position-property-ado.md) è impostato sul byte successivo i dati scritti. Il **scrivere** metodo tronca il resto dei dati in un flusso. Se si desidera troncare tali byte, chiamare [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Se si scrivono corrente [fine del flusso](../../../ado/reference/ado-api/eos-property.md) posizione, la [dimensioni](../../../ado/reference/ado-api/size-property-ado-stream.md) del **flusso** verranno aumentate per contenere eventuali nuovi byte e **fine del flusso** sposterà per il nuovo ultimo byte di **flusso**.  
  
> [!NOTE]
>  Il **scrivere** metodo viene utilizzato con flussi binari ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeBinary**). Per i flussi di testo (**tipo** è **adTypeText**), utilizzare [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo WriteText](../../../ado/reference/ado-api/writetext-method.md)
