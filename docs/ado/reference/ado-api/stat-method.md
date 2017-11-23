---
title: Metodo Stat | Documenti Microsoft
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
f1_keywords: _Stream::Stat
helpviewer_keywords: Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c33383de27f2685849034cec79c6b4589dfb0a79
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
