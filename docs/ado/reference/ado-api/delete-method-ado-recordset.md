---
title: Delete (metodo) (Recordset ADO) | Documenti Microsoft
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
- Recordset15::raw_Delete
- Recordset15::Delete
helpviewer_keywords: Delete method [ADO]
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4f9494c0675c39b4e6441aa62a66a7b6af7daf15
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="delete-method-ado-recordset"></a>Delete (metodo) (Recordset ADO)
Elimina il record corrente o un gruppo di record.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Parametri  
 *AffectRecords*  
 Un [AffectEnum](../../../ado/reference/ado-api/affectenum.md) valore che determina il numero di record di **eliminare** saranno influenzati dal metodo. Il valore predefinito è **adAffectCurrent**.  
  
> [!NOTE]
>  **adAffectAll** e **adAffectAllChapters** non sono argomenti validi per **eliminare**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzo di **eliminare** metodo contrassegna il record corrente o un gruppo di record in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto per l'eliminazione. Se il **Recordset** oggetto non consente l'eliminazione di record, si verifica un errore. Se si è in modalità di aggiornamento immediato, le operazioni di eliminazione si verifica immediatamente nel database. Se non è possibile eliminare un record (a causa di violazioni di integrità del database, ad esempio), il record rimarrà in modalità di modifica dopo la chiamata a [aggiornamento](../../../ado/reference/ado-api/update-method.md). Ciò significa che è necessario annullare l'aggiornamento con [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) prima di spostarsi dal record corrente (ad esempio, con [Chiudi](../../../ado/reference/ado-api/close-method-ado.md), [spostare](../../../ado/reference/ado-api/move-method-ado.md), o [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Se si è in modalità di aggiornamento batch, i record contrassegnati per l'eliminazione dalla cache e l'eliminazione effettiva si verifica quando si chiama il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo. Utilizzare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà per visualizzare i record eliminati.  
  
 Il recupero dei valori di campo del record eliminato genera un errore. Dopo aver eliminato il record corrente, il record eliminato rimane tale finché non si passa a un altro record. Dopo essersi spostati dal record eliminato, non è più accessibile.  
  
 Se si nidificano le eliminazioni in una transazione, è possibile recuperare i record eliminati con la [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) metodo. Se si è in modalità di aggiornamento batch, è possibile annullare l'eliminazione in sospeso o un gruppo di eliminazioni in sospeso con il [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodo.  
  
 Se il tentativo di eliminare i record non riesce a causa di un conflitto con i dati sottostanti (ad esempio, un record è già stato eliminato da un altro utente), il provider restituisce avvisi per il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) raccolta ma non interrompe l'applicazione esecuzione. Errore di run-time si verifica solo se sono presenti conflitti in tutti i record richiesti.  
  
 Se il [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) proprietà dinamica è impostata e il **Recordset** è il risultato dell'esecuzione di un'operazione di JOIN in più tabelle, il **eliminare** elimineranno (metodo) le righe dalla tabella menzionata nel [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Delete (VB)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Esempio del metodo Delete (VBScript)](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Esempio del metodo Delete (VC + +)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Metodo Delete (insieme Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Metodo Delete (insieme Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Metodo DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
