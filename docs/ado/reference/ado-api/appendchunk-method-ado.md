---
title: Metodo AppendChunk (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ba8020b9bf2666ba3b2ab0ffe9156c771360c95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="appendchunk-method-ado"></a>Metodo AppendChunk (ADO)
Aggiunge dati a un testo di grandi dimensioni o dati binari [campo](../../../ado/reference/ado-api/field-object.md), o a un [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Parametri  
 *oggetto*  
 Oggetto **campo** o **parametro** oggetto.  
  
 *Dati*  
 Oggetto **Variant** che contiene i dati da aggiungere all'oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **AppendChunk** metodo su un **campo** o **parametro** oggetto per inserirvi dati long binari o character. In situazioni in cui la memoria di sistema è limitata, è possibile utilizzare il **AppendChunk** metodo per modificare i valori lunghi nelle parti anziché nella loro interezza.  
  
## <a name="field"></a>Campo  
 Se il **adFldLong** bit il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà di un **campo** oggetto è impostato su **true**, è possibile utilizzare il  **AppendChunk** metodo per tale campo.  
  
 Il primo **AppendChunk** chiamare su un **campo** oggetto scrive dati nel campo, sovrascrivendo i dati esistenti. Le successive **AppendChunk** aggiungono chiamate ai dati esistenti. Se si stanno aggiungendo dei dati a un campo e quindi impostare o leggere il valore di un altro campo del record corrente, si presume che si è terminato l'aggiunta di dati e il primo campo. Se si chiama il **AppendChunk** metodo nel primo campo, ADO interpreta la chiamata come nuovo **AppendChunk** operazione e sovrascrive i dati esistenti. L'accesso ai campi in altre [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) gli oggetti che non siano cloni del primo **Recordset** oggetto non altererà **AppendChunk** operazioni.  
  
 Se è presente alcun record corrente quando si chiama **AppendChunk** su un **campo** dell'oggetto, si verifica un errore.  
  
> [!NOTE]
>  Il **AppendChunk** metodo non funziona su **campo** gli oggetti di un [Record ADO (Object)](../../../ado/reference/ado-api/record-object-ado.md) oggetto. Esegue alcuna operazione e genererà un errore di run-time.  
  
## <a name="parameter"></a>Parametro  
 Se il **adParamLong** bit il **attributi** proprietà di un **parametro** oggetto è impostato su **true**, è possibile utilizzare il  **AppendChunk** metodo per tale parametro.  
  
 Il primo **AppendChunk** chiamare su un **parametro** oggetto scrive i dati per il parametro, sovrascrivendo i dati esistenti. Le successive **AppendChunk** chiama su una **parametro** oggetto aggiungere ai dati di parametro esistente. Un **AppendChunk** chiamata che passa un valore null Elimina tutti i dati del parametro.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [AppendChunk e metodi GetChunk (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk e metodi GetChunk (VC + +)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Proprietà Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [Metodo GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
