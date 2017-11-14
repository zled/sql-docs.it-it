---
title: Metodo GetChunk (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4972e08f1db08bde4cdb1241fa36895f2f33ad7b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getchunk-method-ado"></a>Metodo GetChunk (ADO)
Restituisce tutto o in parte, il contenuto di un testo di grandi dimensioni o dati binari [campo](../../../ado/reference/ado-api/field-object.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant**.  
  
#### <a name="parameters"></a>Parametri  
 *Dimensione*  
 Oggetto **lungo** espressione che è uguale al numero di byte o caratteri che si desidera recuperare.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **GetChunk** metodo su un **campo** oggetto per recuperare una parte o tutti i dati long binary o character. In situazioni in cui la memoria di sistema è limitata, è possibile utilizzare il **GetChunk** metodo per modificare i valori lunghi nelle parti, anziché nella loro interezza.  
  
 I dati che un **GetChunk** chiamata viene assegnato a *variabile*. Se *dimensioni* è maggiore di dati restanti, la **GetChunk** il metodo restituisce solo i dati rimanenti senza spaziatura interna *variabile* con spazi vuoti. Se il campo è vuoto, il **GetChunk** metodo restituisce un valore null.  
  
 Ogni successivo **GetChunk** chiamata recupera i dati a partire dalla posizione precedente **GetChunk** chiamata è stata interrotta. Tuttavia, se si recuperano dati da un campo e quindi impostare o leggere il valore di un altro campo del record corrente, ADO presuppone di che avere il recupero dei dati dal primo campo. Se si chiama il **GetChunk** metodo nel primo campo, ADO interpreta la chiamata come nuovo **GetChunk** operazione e avvia la lettura dall'inizio dei dati. L'accesso ai campi in altre [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) gli oggetti che non siano cloni del primo **Recordset** oggetto non altererà **GetChunk** operazioni.  
  
 Se il **adFldLong** bit il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà di un **campo** oggetto è impostato su **True**, è possibile utilizzare il **GetChunk**  metodo per tale campo.  
  
 Se è presente alcun record corrente quando si utilizza il **GetChunk** metodo su un **campo** dell'oggetto, si verifica l'errore 3021 (Nessun record corrente).  
  
> [!NOTE]
>  Il **GetChunk** metodo non funziona su **campo** gli oggetti di un [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto. Esegue alcuna operazione e genererà un errore di run-time.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [AppendChunk e metodi GetChunk (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk e metodi GetChunk (VC + +)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Metodo AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Proprietà Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)

