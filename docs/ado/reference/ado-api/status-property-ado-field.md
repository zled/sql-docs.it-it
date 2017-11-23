---
title: "Proprietà Status (campo ADO) | Documenti Microsoft"
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
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords: Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6db998d81ce756eb68633fb5778c4e8f3633c05
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="status-property-ado-field"></a>Proprietà Status (campo ADO)
Indica lo stato di un [campo](../../../ado/reference/ado-api/field-object.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) valore. Il valore predefinito è **adFieldOK**.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="record-field-status"></a>Stato dei campi di record  
 Imposta sul valore di un **campo** oggetto nella raccolta di campi di un [Record](../../../ado/reference/ado-api/record-object-ado.md) vengono memorizzate nella cache fino a quando l'oggetto [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo viene chiamato. A questo punto, la modifica il valore del campo ha causato un errore, OLE DB genera l'errore **DB_E_ERRORSOCCURRED** (2147749409). La proprietà di stato di uno qualsiasi del **campo** gli oggetti di **campi** insieme che ha causato l'errore sarà presente un valore dal [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) che descrive la causa del il problema.  
  
 Per migliorare le prestazioni, aggiunte ed eliminazioni per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insiemi di **Record** vengono memorizzate nella cache fino a quando il **aggiornamento** metodo viene chiamato e quindi le modifiche vengono eseguite in un aggiornamento ottimistico batch. Se il **aggiornamento** non viene chiamato, il server non è aggiornato. Se tutti gli aggiornamenti non viene restituito un errore del provider OLE DB (DB_E_ERRORSOCCURRED) e **stato** proprietà indica la somma dei valori del codice di stato errore e l'operazione. Ad esempio, **adFieldPendingInsert o eliminato**. Il **stato** proprietà per ogni **campo** può essere usato per stabilire perché il **campo** non aggiunto, modificato o eliminato.  
  
 Molti tipi di problemi rilevati durante l'aggiunta, modifica o eliminazione di un **campo** sono segnalati tramite la **stato** proprietà. Ad esempio, se l'utente elimina un **campo**, è contrassegnato per l'eliminazione di **campi** insieme. Se il successivo **aggiornamento** restituisce un errore perché l'utente ha tentato di eliminare un **campo** per cui non dispongano dell'autorizzazione, il **campo** avrà un  **Stato** di **adFieldPermissionDenied o adFieldPendingDelete**. La chiamata di [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo valori originali di ripristino e imposta il **stato** per **adFieldOK**.  
  
 Analogamente, il **aggiornamento** metodo può restituire un errore perché un nuovo **campo** è stato aggiunto e assegnargli un valore appropriato. In tal caso il nuovo **campo** verrà incluso il **campi** insieme e lo stato del **adFieldPendingInsert** ed eventualmente **adFieldCantCreate** (a seconda del provider). È possibile fornire un valore appropriato per il nuovo **campo** e chiamare **aggiornamento** nuovamente.  
  
## <a name="recordset-field-status"></a>Stato dei campi di recordset  
 Imposta sul valore di un **campo** oggetto nella raccolta di campi di uno un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) vengono memorizzati nella cache fino a quando l'oggetto [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo viene chiamato. A questo punto, la modifica il valore del campo ha causato un errore, OLE DB genera l'errore **DB_E_ERRORSOCCURRED** (2147749409). La proprietà di stato di uno qualsiasi del **campo** gli oggetti di **campi** insieme che ha causato l'errore sarà presente un valore dal [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) che descrive la causa del il problema.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Status (campo) (VB)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Esempio di proprietà Status (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
