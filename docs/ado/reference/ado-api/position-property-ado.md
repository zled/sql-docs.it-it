---
title: "Posizione, proprietà (ADO) | Documenti Microsoft"
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
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 76a3d94b97fa32e372cd6cc67367450d2f62530b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="position-property-ado"></a>Proprietà Position (ADO)
Indica la posizione corrente all'interno di un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che specifica l'offset, in numero di byte, della posizione corrente dall'inizio del flusso. Il valore predefinito è 0, che rappresenta il primo byte nel flusso.  
  
## <a name="remarks"></a>Osservazioni  
 La posizione corrente può essere spostata in un punto dopo la fine del flusso. Se si specifica la posizione corrente oltre la fine del flusso di [dimensioni](../../../ado/reference/ado-api/size-property-ado-stream.md) del **flusso** oggetto verrà aumentato di conseguenza. Eventuali nuovi byte aggiunti in questo modo sarà null.  
  
> [!NOTE]
>  **Posizione** misura sempre byte. Per i flussi di testo con caratteri multibyte, moltiplicare la posizione per le dimensioni del carattere per determinare il numero di caratteri. Ad esempio, per un set di caratteri a due byte, il primo carattere è nella posizione 0, il secondo carattere nella posizione 2, il terzo carattere nella posizione 4 e così via.  
  
> [!NOTE]
>  Valori negativi non possono essere utilizzati per modificare la posizione corrente in un **flusso**. È possono utilizzare solo numeri positivi per **posizione**.  
  
> [!NOTE]
>  Per sola lettura **flusso** gli oggetti ADO non restituirà un errore se **posizione** è impostata su un valore maggiore di **dimensioni** del **flusso**. Ciò non modifica le dimensioni del **flusso**, o si modifica il **flusso** contenuto in alcun modo. Tuttavia, questa operazione deve essere evitata poiché ciò comporta un significativo **posizione**valore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà set di caratteri (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
