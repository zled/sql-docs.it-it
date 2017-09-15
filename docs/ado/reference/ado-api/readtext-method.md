---
title: Metodo ReadText | Documenti Microsoft
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
- _Stream::raw_ReadText
- _Stream::ReadText
helpviewer_keywords:
- ReadText method [ADO]
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b134e064cc3d1dfa06c5d948d74e49f643756bd1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="readtext-method"></a>Metodo ReadText
Legge un numero di caratteri da un testo specificato [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Parametri  
 *NumChars*  
 Facoltativa. Oggetto **lungo** valore che specifica il numero di caratteri da leggere dal file o un [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) valore. Il valore predefinito è **adReadAll**.  
  
## <a name="return-value"></a>Valore restituito  
 Il **ReadText** metodo legge un numero specificato di caratteri, un'intera riga o dell'intero flusso da un **flusso** dell'oggetto e restituisce la stringa risulta.  
  
## <a name="remarks"></a>Osservazioni  
 Se *NumChar* è maggiore del numero di caratteri rimanenti nel flusso, vengono restituiti solo i caratteri rimanenti. La stringa letta non possono essere riempita per corrispondere alla lunghezza specificata da *NumChar*. Se non sono presenti caratteri rimanenti da leggere, viene restituito un variant il cui valore è null. **ReadText** non può essere usato per leggere le versioni precedenti.  
  
> [!NOTE]
>  Il **ReadText** metodo viene utilizzato con flussi di testo ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**). Per i flussi binari (**tipo** è **adTypeBinary**), utilizzare [lettura](../../../ado/reference/ado-api/read-method.md).  
  
 Le query che generano una grande quantità di dati XML restituiti tramite il **ReadText** metodo dell'oggetto flusso di dati oggetto ADO (ActiveX) può richiedere una notevole quantità di tempo per l'esecuzione; se questa operazione viene eseguita in un componente COM+ che viene richiamato da un Pagina ASP, la sessione dell'utente può verificarsi un timeout. ADO converte i dati oggetto di flusso dalla codifica UTF-8 in formato Unicode; la riallocazione di memoria frequente coinvolto nella conversione di una grande quantità di dati è piuttosto lunga. Per risolvere, effettuare chiamate ripetute al **ReadText** metodo ADO oggetto command e specificare un numero minore di caratteri. I test hanno dimostrato che un valore equivalente a 128 KB (131.072) è ottimale. Tempo di risposta diminuisce quando questo valore è ridotto. Per ulteriori informazioni, vedere l'articolo della Knowledge Base 280067, "PRB: recupero di documenti XML molto grandi da SQL Server 2000 utilizzando il metodo ReadText dell'oggetto flusso ADO potrebbe risultare lento", nella Microsoft Knowledge Base in http://support.microsoft.com.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Read, metodo](../../../ado/reference/ado-api/read-method.md)
