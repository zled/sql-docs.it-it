---
title: Metodo Resync | Documenti Microsoft
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
f1_keywords:
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords: Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8fe3a2a123061cd0fc4de31d2b08ab82d41f7542
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="resync-method"></a>Risincronizzazione (metodo)
Aggiorna i dati nell'oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, o [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto dal database sottostante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Parametri  
 *AffectRecords*  
 Facoltativa. Un [AffectEnum](../../../ado/reference/ado-api/affectenum.md) valore che determina il numero di record di **Resync** saranno influenzati dal metodo. Il valore predefinito è **adAffectAll**. Questo valore non è disponibile con il **Resync** metodo il **campi** raccolta di un **Record** oggetto.  
  
 *ResyncValues*  
 Facoltativa. Oggetto [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md) valore che specifica se i valori sottostanti vengono sovrascritti. Il valore predefinito è **adResyncAllValues**.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="recordset"></a>recordset  
 Utilizzare il **Resync** metodo risincronizzare i record nell'oggetto **Recordset** con il database sottostante. Ciò è utile se si utilizza un cursore statico o forward-only, ma si desidera visualizzare tutte le modifiche nel database sottostante.  
  
 Se si imposta la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**, **Resync** è disponibile solo per non di sola lettura **Recordset** oggetti.  
  
 A differenza di [Requery](../../../ado/reference/ado-api/requery-method.md) (metodo), il **Resync** metodo non viene eseguito nuovamente il **Recordset** sottostante del comando. Nuovi record nel database sottostante non saranno visibili.  
  
 Se il tentativo di risincronizzare non riesce a causa di un conflitto con i dati sottostanti (ad esempio, un record è stato eliminato da un altro utente), il provider restituisce avvisi per il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) si verifica un errore di run-time e di raccolta. Utilizzare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà (**adFilterConflictingRecords**) e [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà per individuare i record con conflitti.  
  
 Se il [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) e [Resync Command](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) vengono impostate le proprietà dinamiche e **Recordset** è il risultato dell'esecuzione di un'operazione di JOIN più tabelle, quindi il  **Risincronizzazione** metodo verrà eseguito il comando specificato nella **Resync Command** proprietà solo per la tabella denominata nel **tabella univoca** proprietà.  
  
## <a name="fields"></a>Campi  
 Utilizzare il **Resync** metodo risincronizzare i valori del **campi** raccolta di un **Record** oggetto con l'origine dati sottostante. Il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà non è interessata da questo metodo.  
  
 Se *ResyncValues* è impostato su **adResyncAllValues** (valore predefinito), il [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md), [valore](../../../ado/reference/ado-api/value-property-ado.md), e [ OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) le proprietà di [campo](../../../ado/reference/ado-api/field-object.md) gli oggetti nella raccolta sono sincronizzati. Se *ResyncValues* è impostato su **adResyncUnderlyingValues**, solo il **UnderlyingValue** proprietà è sincronizzata.  
  
 Il valore di **stato** proprietà per ogni **campo** oggetto al momento della chiamata influisce anche sul comportamento di **Resync**. Per **campo** gli oggetti che hanno **stato** valori di **su adFieldPendingUnknown** o **adFieldPendingInsert**, **Resync**  non ha alcun effetto. Per **stato** valori di **uguali a adFieldPendingChange** o **adFieldPendingDelete**, **Resync** Sincronizza i valori dei dati per i campi che ancora presenti nell'origine dati.  
  
 **Risincronizzazione** non modificherà **stato** valori di **campo** oggetti a meno che non si verifica un errore quando **Resync** viene chiamato. Ad esempio, se il campo non esiste più, il provider restituirà un oggetto appropriato **stato** valore per il **campo** dell'oggetto, ad esempio **adFieldDoesNotExist**. Restituito **stato** valori possono essere combinati logicamente all'interno del valore del **stato** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Raccolta Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo (VB) Resync](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Metodo esempio Resync (VC + +)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Clear (metodo) (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Proprietà UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
