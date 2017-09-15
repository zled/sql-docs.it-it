---
title: Metodo Stat | Documenti Microsoft
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
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c19b5bed54d4bbb27a5aeb235b0e4ab529b9c836
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="stat-method"></a>Metodo Stat
Recupera le informazioni su un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **lungo** valore che indica lo stato dell'operazione.  
  
#### <a name="parameters"></a>Parametri  
 *StatStg*  
 Struttura STATSTG che verrà compilata con informazioni sul flusso. L'implementazione del **Stat** metodo utilizzata dall'oggetto flusso ADO non inserire tutti i campi della struttura.  
  
 *StatFlag*  
 Specifica che questo metodo non restituisce alcuni dei membri nella struttura STATSTG, risparmiando un'operazione di allocazione di memoria. I valori provengono dall'enumerazione STATFLAG. L'enumerazione STATFLAG include due valori  
  
|Costante|Valore|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|NON|1|  
  
## <a name="remarks"></a>Osservazioni  
 La versione del metodo Stat implementato per l'oggetto flusso ADO vengono compilati i seguenti campi della struttura STATSTG:  
  
 *pwcsName*  
 Stringa contenente il nome del flusso, se disponibile e il valore di StatFlag non è stata specificata.  
  
 *cbSize*  
 Specifica le dimensioni in byte del flusso o byte della matrice.  
  
 *mtime*  
 Indica l'ora dell'ultima modifica per l'archiviazione, flusso o matrice di byte.  
  
 *CTime*  
 Indica l'ora di creazione di questa archiviazione, flusso o matrice di byte.  
  
 *per volta*  
 Indica l'ora dell'ultimo accesso per l'archiviazione, flusso o matrice di byte.  
  
 Se viene specificato nel parametro StatFlag, il nome del flusso non viene restituito.  
  
 Se non viene specificato nel parametro StatFlag e nessun nome è disponibile per il flusso corrente, questo valore sarà E_NOTIMPL.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)