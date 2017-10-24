---
title: Metodo CancelBatch (ADO) | Documenti Microsoft
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
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2eced52fb03d47d8f79838d07a45c1d8dde31cf9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cancelbatch-method-ado"></a>Metodo CancelBatch (ADO)
Annulla un aggiornamento batch in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Parametri  
 *AffectRecords*  
 Facoltativa. Un [AffectEnum](../../../ado/reference/ado-api/affectenum.md) valore che indica il numero di record di **CancelBatch** saranno influenzati dal metodo.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CancelBatch** metodo annullare eventuali aggiornamenti in sospeso in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in modalità di aggiornamento batch. Se il **Recordset** è in modalità di aggiornamento immediato, la chiamata **CancelBatch** senza **adAffectCurrent** genera un errore.  
  
 Se si sta modificando il record corrente o aggiungendo un nuovo record quando si chiama **CancelBatch**, ADO prima chiama il [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo per annullare eventuali modifiche memorizzate nella cache. Dopo che tutte le modifiche in sospeso il **Recordset** vengono annullate.  
  
 Il record corrente potrebbe essere dopo un **CancelBatch** chiama, in particolare se era in corso l'aggiunta di un nuovo record. Per questo motivo, è consigliabile impostare la posizione corrente in un percorso noto nel **Recordset** dopo il **CancelBatch** chiamare. Ad esempio, chiamare il [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) metodo.  
  
 Se il tentativo di annullare gli aggiornamenti in sospeso non riesce a causa di un conflitto con i dati sottostanti (ad esempio, se un record è stato eliminato da un altro utente), il provider restituisce avvisi per il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) raccolta ma non interrompe esecuzione del programma. Errore di run-time si verifica solo se sono presenti conflitti in tutti i record richiesti. Utilizzare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà (**adFilterAffectedRecords**) e [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà per individuare i record con conflitti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio UpdateBatch e CancelBatch metodi (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Esempio UpdateBatch e CancelBatch metodi (VC + +)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel (metodo) (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Metodo CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Clear (metodo) (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Proprietà LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)

