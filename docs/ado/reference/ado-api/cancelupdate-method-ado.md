---
title: Metodo CancelUpdate (ADO) | Documenti Microsoft
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
- Recordset15::CancelUpdate
helpviewer_keywords:
- CancelUpdate method [ADO]
ms.assetid: eaa856cc-c786-462e-890c-c896261b1741
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd858ec4d40f307027a75fa657c4e4d2b0539064
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="cancelupdate-method-ado"></a>Metodo CancelUpdate (ADO)
Annulla le modifiche apportate alla riga corrente o nuova di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, o [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto, prima di chiamare il [aggiornamento ](../../../ado/reference/ado-api/update-method.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="recordset"></a>recordset  
 Utilizzare il **CancelUpdate** metodo per annullare le modifiche apportate alla riga corrente o per eliminare una riga appena aggiunta. Non è possibile annullare le modifiche apportate alla riga corrente o a una nuova riga dopo la chiamata di **aggiornamento** (metodo), a meno che le modifiche siano parte di una transazione di cui è possibile eseguire il rollback con il [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) metodo, o parte di un aggiornamento batch. Nel caso di un aggiornamento batch, è possibile annullare il **aggiornare** con il **CancelUpdate** o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodo.  
  
 Se si aggiunge una nuova riga quando si chiama il **CancelUpdate** (metodo), la riga corrente diventa la riga corrente prima di [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) chiamare.  
  
 Se in modalità modifica e si desidera spostarsi dal record corrente (ad esempio, tramite il [spostare](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), o [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodi), è possibile utilizzare  **CancelUpdate** per annullare le modifiche in sospeso. Potrebbe essere necessario eseguire questa operazione se l'aggiornamento non è possibile inviare all'origine dati. Ad esempio, un tentativo di eliminazione che ha esito negativo a causa di violazioni di integrità referenziale manterrà il **Recordset** in modalità di modifica dopo una chiamata a [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md).  
  
## <a name="record"></a>Record  
 Il **CancelUpdate** metodo annulla gli inserimenti o eliminazioni di in sospeso [campo](../../../ado/reference/ado-api/field-object.md) oggetti, Annulla gli aggiornamenti dei campi esistenti in sospeso e li Ripristina i valori originali. Il [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà di tutti i campi di **campi** insieme in **adFieldOK**.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Raccolta Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi CancelUpdate (VB) e di aggiornamento](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Esempio di metodi CancelUpdate (VC + +) e di aggiornamento](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew (metodo) (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Cancel (metodo) (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Metodo CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Proprietà EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Metodo Update](../../../ado/reference/ado-api/update-method.md)
