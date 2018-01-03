---
title: Metodo WriteText | Documenti Microsoft
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
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords: WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c744551b835ce814f8a6baf9781e04e67b6139d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="writetext-method"></a>Metodo WriteText
Scrive una stringa di testo specificato in un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Parametri  
 *Dati*  
 Oggetto **stringa** valore che contiene il testo in caratteri da scrivere.  
  
 *Opzioni*  
 Facoltativo. Oggetto [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) valore che indica se un carattere separatore di riga deve essere scritto alla fine della stringa specificata.  
  
## <a name="remarks"></a>Osservazioni  
 Stringhe specificate vengono scritti i **flusso** oggetto senza spazi intermedi o caratteri tra ogni stringa.  
  
 Corrente [posizione](../../../ado/reference/ado-api/position-property-ado.md) è impostata sul carattere che segue i dati scritti. Il **WriteText** metodo tronca il resto dei dati in un flusso. Se si desidera troncare questi caratteri, chiamare [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Se si scrivono corrente [fine del flusso](../../../ado/reference/ado-api/eos-property.md) posizione, la [dimensioni](../../../ado/reference/ado-api/size-property-ado-stream.md) del **flusso** verranno aumentate per contenere i caratteri di nuova, e **fine del flusso** spostare il nuovo ultimo byte di **flusso**.  
  
> [!NOTE]
>  Il **WriteText** metodo viene utilizzato con flussi di testo ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**). Per i flussi binari (**tipo** è **adTypeBinary**), utilizzare [scrivere](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Write](../../../ado/reference/ado-api/write-method.md)
