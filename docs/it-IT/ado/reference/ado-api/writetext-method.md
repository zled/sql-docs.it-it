---
title: Metodo WriteText | Documenti Microsoft
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
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dda7b8a8aa215f43cadfc080a1d0df24b7c94e0d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
 Facoltativa. Oggetto [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) valore che indica se un carattere separatore di riga deve essere scritto alla fine della stringa specificata.  
  
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
