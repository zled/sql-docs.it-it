---
title: "Proprietà AbsolutePosition (ADO) | Documenti Microsoft"
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
f1_keywords: Recordset15::AbsolutePosition
helpviewer_keywords: AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 491ed39340dd066955db2fd73ed986614744cff4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="absoluteposition-property-ado"></a>Proprietà AbsolutePosition (ADO)
Indica la posizione ordinale di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) record corrente dell'oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Per il codice a 32 bit, imposta o restituisce un **lungo** valore compreso tra 1 e il numero di record nel **Recordset** oggetto ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)), oppure restituisce uno del [ PositionEnum](../../../ado/reference/ado-api/positionenum.md) valori.  
  
 Per il codice a 64 bit, utilizzare un tipo di dati che fornisce per l'archiviazione di un valore a 64 bit. Ad esempio, è possibile utilizzare Long o un altro valore che è a 64 bit di lunghezza, ad esempio DBORDINAL. Non utilizzare **PositionEnum** valori poiché sono limitati alla lunghezza di 32 bit.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostare il **AbsolutePosition** proprietà ADO richiede che il provider OLE DB in uso è stato implementato il [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx) interfaccia.  
  
 L'accesso di **AbsolutePosition** proprietà di un **Recordset** che è stato aperto con forward-only o dinamici del cursore genera l'errore **adErrFeatureNotAvailable**. Gli altri tipi di cursore, verrà restituita nella posizione corretta fino a quando il provider OLE DB supporta il **IRowsetScroll:IRowsetLocate** interfaccia. Se il provider non supporta il **IRowsetScroll** interfaccia, la proprietà è impostata su **adPosUnknown**. Vedere la documentazione relativa al provider per determinare se supporta **IRowsetScroll**.  
  
 Utilizzare il **AbsolutePosition** proprietà per passare a un record in base alla posizione ordinale di **Recordset** oggetto, o per determinare la posizione ordinale del record corrente. Il provider deve supportare le funzionalità appropriate per questa proprietà sia disponibile.  
  
 Ad esempio il [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) proprietà, **AbsolutePosition** è basata su 1 ed è uguale a 1 quando il record corrente è il primo record di **Recordset**. È possibile ottenere il numero totale di record di **Recordset** dell'oggetto dal [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) proprietà.  
  
 Quando si imposta la **AbsolutePosition** proprietà, anche se a un record nella cache corrente, ADO ricarica la cache con un nuovo gruppo di record che iniziano con il record specificato. Il [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) proprietà determina le dimensioni di questo gruppo.  
  
> [!NOTE]
>  Non è consigliabile utilizzare il **AbsolutePosition** proprietà come numero di record sostitutivo. La posizione di un determinato record cambia quando si elimina un record precedente. Non vi è alcuna garanzia che un determinato record avrà lo stesso **AbsolutePosition** se il **Recordset** oggetto viene rieseguito o riaperto. I segnalibri sono ancora il modo consigliato per mantenere e tornare a una posizione specifica e sono l'unico modo il posizionamento in tutti i tipi di **Recordset** oggetti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio AbsolutePosition e CursorLocation proprietà (Visual Basic)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [Esempio AbsolutePosition e CursorLocation proprietà (VC + +)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [Proprietà AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Proprietà RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
