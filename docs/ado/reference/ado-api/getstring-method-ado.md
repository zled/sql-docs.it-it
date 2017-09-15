---
title: Metodo GetString (ADO) | Documenti Microsoft
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
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d146c1cdd2ebb4f069afef7163ce998cbb149ef6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getstring-method-ado"></a>Metodo GetString (ADO)
Restituisce il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sotto forma di stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il **Recordset** come una stringa con valori di **Variant** (BSTR).  
  
#### <a name="parameters"></a>Parametri  
 *StringFormat*  
 Oggetto [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) valore che specifica il modo in **Recordset** devono essere convertite in una stringa. Il *RowDelimiter*, *ColumnDelimiter*, e *NullExpr* parametri vengono utilizzati solo con un *StringFormat* di ** adClipString**.  
  
 *NumRows*  
 Facoltativa. Il numero di righe da convertire nel **Recordset**. Se *NumRows* non viene specificato, o se è maggiore del numero totale di righe nel **Recordset**, quindi tutte le righe di **Recordset** vengono convertiti.  
  
 *ColumnDelimiter*  
 Facoltativa. Delimitatore utilizzato tra le colonne, se specificato, in caso contrario il carattere di tabulazione.  
  
 *RowDelimiter*  
 Facoltativa. Un delimitatore utilizzato tra righe, se specificato, in caso contrario il carattere di ritorno a capo.  
  
 *NullExpr*  
 Facoltativa. Un'espressione utilizzata al posto di un valore null, se specificato, in caso contrario la stringa vuota.  
  
## <a name="remarks"></a>Osservazioni  
 Dati di riga, ma non i dati dello schema, viene salvato nella stringa. Pertanto, un **Recordset** non può essere riaperto utilizzando questa stringa.  
  
 Questo metodo è equivalente al RDO **GetClipString** metodo.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo GetString (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
