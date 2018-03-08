---
title: Metodo CopyRecord (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4c31ec2491486c6c2332e32395246db4651f4e8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="copyrecord-method-ado"></a>Metodo CopyRecord (ADO)
Copia di un'entità rappresentata da un [record](../../../ado/reference/ado-api/record-object-ado.md) in un'altra posizione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **stringa** valore che contiene un URL che specifica l'entità da copiare (ad esempio, un file o directory). Se *origine* viene omesso o specifica una stringa vuota, il file o directory rappresentata dall'oggetto corrente [Record](../../../ado/reference/ado-api/record-object-ado.md) verranno copiati.  
  
 *Destinazione*  
 Facoltativa. Oggetto **stringa** valore contenente un URL che specifica la posizione in cui *origine* verranno copiati.  
  
 *UserName*  
 Facoltativa. Oggetto **stringa** valore che contiene l'ID utente, se necessario, si autorizza l'accesso a *destinazione*.  
  
 *Password*  
 Facoltativa. Oggetto **stringa** valore contenente la password, se necessario, verifica *UserName*.  
  
 *Opzioni*  
 Facoltativa. Oggetto [CopyRecordOptionsEnum uguale al](../../../ado/reference/ado-api/copyrecordoptionsenum.md) valore con un valore predefinito di **adCopyUnspecified**. Specifica il comportamento di questo metodo.  
  
 *Async*  
 Facoltativa. Oggetto **booleano** valore che, quando **True**, specifica che questa operazione deve essere asincrona.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** valore restituito in genere il valore di *destinazione*. Tuttavia, il valore esatto restituito è dipende dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di *origine* e *destinazione* non deve essere identica; in caso contrario, si verifica un errore di run-time. Almeno uno dei nomi di server, percorso o risorsa deve essere diverso.  
  
 Tutti gli elementi figlio (ad esempio, le sottodirectory) di *origine* vengono copiati in modo ricorsivo, a meno che non **adCopyNonRecursive** specificato. In un'operazione ricorsiva, *destinazione* non deve essere una sottodirectory di *origine*; in caso contrario, l'operazione non verrà completata.  
  
 Questo metodo ha esito negativo se *destinazione* identifica un'entità esistente (ad esempio, un file o una directory), a meno che non **adCopyOverWrite** specificato.  
  
> [!IMPORTANT]
>  Utilizzare il **adCopyOverWrite** opzione con cautela. Ad esempio, se si specifica questa opzione quando si copia un file in una directory verrà *eliminare* la directory e sostituirlo con il file.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
