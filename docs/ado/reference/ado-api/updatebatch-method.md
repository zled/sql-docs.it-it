---
title: Metodo UpdateBatch | Documenti Microsoft
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
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 57c85b6ed83792e2e489eb91dab59bd0da598939
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updatebatch-method"></a>Metodo UpdateBatch
Scrive tutti gli aggiornamenti di batch in sospeso sul disco.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Parametri  
 *AffectRecords*  
 Facoltativa. Un [AffectEnum](../../../ado/reference/ado-api/affectenum.md) valore che indica il numero di record di **UpdateBatch** saranno influenzati dal metodo.  
  
 *PreserveStatus*  
 Facoltativa. Oggetto **booleano** valore che specifica se le modifiche locali, come indicato dal [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà, deve essere eseguito il commit. Se questo valore è impostato su **True**, **stato** proprietà di ogni record rimane invariata dopo il completamento dell'aggiornamento.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **UpdateBatch** metodo quando si modifica un **Recordset** oggetto in modalità di aggiornamento batch per trasmettere tutte le modifiche apportate un **Recordset** oggetto al database sottostante.  
  
 Se il **Recordset** oggetto supporta l'aggiornamento in batch, è possibile memorizzare nella cache più modifiche a uno o più record localmente finché non si chiama il **UpdateBatch** metodo. Se si modifica il record corrente o aggiungendo un nuovo record quando si chiama il **UpdateBatch** (metodo), ADO chiamerà automaticamente il [aggiornamento](../../../ado/reference/ado-api/update-method.md) per salvare le modifiche in sospeso per il record corrente prima di trasmettere le modifiche in blocco al provider. È consigliabile utilizzare l'aggiornamento in blocco con un solo cursore statico o keyset.  
  
> [!NOTE]
>  Specifica di **adAffectGroup** come valore per questo parametro verrà generato un errore quando non sono presenti record visibili nell'oggetto **Recordset** (ad esempio, un filtro per il quale nessun record corrispondente).  
  
 Se il tentativo di trasmettere le modifiche non riesce per qualsiasi o tutti i record a causa di un conflitto con i dati sottostanti (ad esempio, un record è già stato eliminato da un altro utente), il provider restituisce avvisi per il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme e un si verifica l'errore di run-time. Utilizzare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà (**adFilterAffectedRecords**) e [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà per individuare i record con conflitti.  
  
 Per annullare tutti gli aggiornamenti di batch in sospeso, utilizzare il [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodo.  
  
 Se il [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) e [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) vengono impostate le proprietà dinamiche e **Recordset** è il risultato dell'esecuzione di un'operazione di JOIN in più tabelle, il esecuzione del **UpdateBatch** metodo in modo implicito è seguito dal [Resync](../../../ado/reference/ado-api/resync-method.md) (metodo), a seconda delle impostazioni del [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) proprietà.  
  
 L'ordine in cui i singoli aggiornamenti di un batch vengono eseguiti sull'origine dati non è necessariamente lo stesso ordine in cui sono stati eseguiti in locale **Recordset**. Ordine di aggiornamento è dipende dal provider. Tenerne conto durante la codifica degli aggiornamenti che sono correlati tra loro, ad esempio i vincoli di chiave esterni per un inserimento o aggiornamento.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio UpdateBatch e CancelBatch metodi (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Esempio UpdateBatch e CancelBatch metodi (VC + +)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Clear (metodo) (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Proprietà LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Update (metodo)](../../../ado/reference/ado-api/update-method.md)

