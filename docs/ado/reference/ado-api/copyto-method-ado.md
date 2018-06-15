---
title: CopyTo (metodo) (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15537df53441d0204a62d19ae38b9105c456cddb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277170"
---
# <a name="copyto-method-ado"></a>CopyTo (metodo) (ADO)
Copia il numero specificato di caratteri o byte (in base alle [tipo](../../../ado/reference/ado-api/type-property-ado-stream.md)) nei [flusso](../../../ado/reference/ado-api/stream-object-ado.md) a un altro **flusso** oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Parametri  
 *DestStream*  
 Un valore della variabile oggetto che contiene un riferimento a un oggetto aperto **flusso** oggetto. Corrente **flusso** viene copiato nella destinazione **flusso** specificato da *DestStream*. La destinazione **flusso** deve essere già aperta. In caso contrario, si verifica un errore di run-time.  
  
> [!NOTE]
>  Il *DestStream* parametro non può essere un proxy di **flusso** oggetto perché è necessario l'accesso a un'interfaccia privata sul **flusso** oggetto che non può essere eseguita in modalità remota per il client.  
  
 *NumChars*  
 Facoltativo. Un **intero** valore che specifica il numero di byte o caratteri da copiare dalla posizione corrente nell'origine **flusso** alla destinazione **flusso**. Il valore predefinito è -1, che specifica che tutti i caratteri o byte vengono copiati dalla posizione corrente a [fine del flusso](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Remarks  
 Questo metodo copia il numero specificato di caratteri o byte, a partire dalla posizione corrente specificata dal [posizione](../../../ado/reference/ado-api/position-property-ado.md) proprietà. Se il numero specificato è maggiore del numero di byte fino a quando disponibile **fine del flusso**, quindi solo caratteri o byte dalla posizione corrente per **fine del flusso** vengono copiati. Se il valore di *NumChars* è -1 o viene omesso, vengono copiati tutti i caratteri o byte a partire dalla posizione corrente.  
  
 Se sono presenti caratteri o byte nel flusso di destinazione, rimane oltre il punto in cui termina la copia tutto il contenuto e non viene troncato. **Posizione** diventa il byte immediatamente dopo l'ultimo byte copiato. Se si desidera troncare tali byte, chiamare [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 **CopyTo** deve essere utilizzato per copiare i dati a una destinazione **flusso** dello stesso tipo dell'origine **flusso** (loro **tipo** le impostazioni delle proprietà sono entrambi **adTypeText** o entrambi **adTypeBinary**). Per il testo **flusso** oggetti, è possibile modificare il [Charset](../../../ado/reference/ado-api/charset-property-ado.md) impostazione della proprietà della destinazione **flusso** per la conversione da un set di caratteri da un altro. Inoltre, il testo **flusso** oggetti possono essere copiati in binario **flusso** gli oggetti, ma binario **flusso** oggetti non possono essere copiati in testo **flusso**  oggetti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
