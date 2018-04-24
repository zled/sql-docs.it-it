---
title: Metodo MoveRecord (ADO) | Documenti Microsoft
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
- _Record::MoveRecord
- _Record::raw_MoveRecord
helpviewer_keywords:
- MoveRecord method [ADO]
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c6361dca137a27c5b54149fd400ee5cd29d9160
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="moverecord-method-ado"></a>Metodo MoveRecord (ADO)
Sposta l'entità rappresentata da un [Record](../../../ado/reference/ado-api/record-object-ado.md) in un'altra posizione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **stringa** valore che contiene un URL che identifica il **Record** da spostare. Se *origine* viene omesso o specifica una stringa vuota, l'oggetto rappresentato da questo **Record** viene spostato. Ad esempio, se il **Record** rappresenta un file, il contenuto del file viene spostati nel percorso specificato da *destinazione*.  
  
 *Destinazione*  
 Facoltativa. Oggetto **stringa** valore contenente un URL che specifica la posizione in cui *origine* verrà spostato.  
  
 *UserName*  
 Facoltativa. Oggetto **stringa** valore che contiene l'ID utente, se necessario, si autorizza l'accesso a *destinazione*.  
  
 *Password*  
 Facoltativa. Oggetto **stringa** che contiene la password che, se necessario, verifica *UserName*.  
  
 *Opzioni*  
 Facoltativa. Oggetto [MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md) valore il cui valore predefinito è **adMoveUnspecified**. Specifica il comportamento di questo metodo.  
  
 *Async*  
 Facoltativa. Oggetto **booleano** valore che, quando **True**, specifica l'operazione deve essere asincrona.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** valore. In genere, il valore di *destinazione* viene restituito. Tuttavia, il valore esatto restituito è dipende dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di *origine* e *destinazione* non deve essere identica; in caso contrario, si verifica un errore di run-time. Almeno i nomi di server, percorso e delle risorse devono essere diverso.  
  
 Per i file spostati utilizzando Internet Publishing Provider, questo metodo aggiorna tutti i collegamenti ipertestuali salvo diversamente specificato da *opzioni*. Questo metodo ha esito negativo se *destinazione* identifica un oggetto esistente (ad esempio, un file o una directory), a meno che non **adMoveOverWrite** specificato.  
  
> [!NOTE]
>  Utilizzare il **adMoveOverWrite** opzione con cautela. Ad esempio, specifica questa opzione durante lo spostamento di un file in una directory, verrà eliminare la directory e sostituirlo con il file.  
  
 Alcuni attributi del **Record** dell'oggetto, ad esempio il [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) proprietà, non verrà aggiornato dopo il completamento dell'operazione. Aggiornare il **Record** proprietà dell'oggetto chiudendo il **Record**, quindi aprirlo nuovamente con l'URL della posizione in cui è stata spostata il file o directory.  
  
 Se questo **Record** ottenuto da un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), il nuovo percorso del file spostato o della directory non vengano riflesse immediatamente nel **Recordset**. Aggiornare il **Recordset** , chiudere e riaprire.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Move (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Metodi MoveFirst, MoveLast, MoveNext e MovePrevious (Servizi Desktop remoto)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
