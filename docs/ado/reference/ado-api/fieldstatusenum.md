---
title: FieldStatusEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
apitype: COM
f1_keywords:
- FieldStatusEnum
helpviewer_keywords:
- FieldStatusEnum enumeration [ADO]
ms.assetid: e06da1e2-303f-41b2-a3b0-61e233da152c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e04f98c5691a66b02a4c5daa8d745f529a9820e0
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/10/2018
---
# <a name="fieldstatusenum"></a>FieldStatusEnum
Specifica il [stato](../../../ado/reference/ado-api/status-property-ado-field.md) di un [campo oggetto](../../../ado/reference/ado-api/field-object.md).  
  
 Il **adFieldPending\***  indica l'operazione che ha causato lo stato da impostare e può essere combinato con altri valori di stato.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adFieldAlreadyExists**|26|Indica che il campo specificato esiste già.|  
|**adFieldBadStatus**|12|Indica che un valore di stato non valido è stato inviato da ADO per il provider OLE DB. Cause possibili includono un OLE DB 1.0 o 1.1 provider o una combinazione non corretta di [valore](../../../ado/reference/ado-api/value-property-ado.md) e [stato](../../../ado/reference/ado-api/status-property-ado-field.md).|  
|**adFieldCannotComplete**|20|Indica che il server dell'URL specificato da [origine](../../../ado/reference/ado-api/source-property-ado-record.md) non è stato possibile completare l'operazione.|  
|**adFieldCannotDeleteSource**|23|Indica che durante un'operazione di spostamento, una struttura o un sottoalbero è stato spostato in un nuovo percorso, ma non è stato possibile eliminare l'origine.|  
|**adFieldCantConvertValue**|2|Indica che il campo non può essere recuperato o archiviato senza perdita di dati.|  
|**adFieldCantCreate**|7|Indica che il campo non può essere aggiunto perché il provider ha superato il limite (ad esempio il numero di campi consentiti).|  
|**adFieldDataOverflow**|6|Indica che i dati restituiti dal provider di overflow rispetto al tipo di dati del campo.|  
|**adFieldDefault**|13|Indica che il valore predefinito per il campo è stato utilizzato durante l'impostazione di dati.|  
|**adFieldDoesNotExist**|16|Indica che il campo specificato non esiste.|  
|**adFieldIgnore**|15|Indica che questo campo è stato ignorato durante l'impostazione dati dei valori nell'origine. Il provider è impostato alcun valore.|  
|**adFieldIntegrityViolation**|10|Indica che il campo non può essere modificato perché è un'entità calcolata o derivata.|  
|**adFieldInvalidURL**|17|Indica che l'URL dell'origine dati contiene caratteri non validi.|  
|**adFieldIsNull**|3|Indica che il provider ha restituito un valore VARIANT di tipo VT_NULL e che il campo non è vuoto.|  
|**adFieldOK**|0|Valore predefinito. Indica che il campo è stato correttamente aggiunto o eliminato.|  
|**adFieldOutOfSpace**|22|Indica che il provider non riesce a ottenere spazio di archiviazione sufficiente per completare un'operazione di spostamento o l'operazione di copia.|  
|**adFieldPendingChange**|0x40000|Indica che il campo è stato eliminato e quindi riaggiunte, magari con un tipo di dati diverso oppure che il valore del campo in precedenza, era stato di **adFieldOK** è stato modificato. Verrà modificato il formato finale del campo di [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta dopo il [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo viene chiamato.|  
|**adFieldPendingDelete**|0x20000|Indica che il **eliminare** l'operazione ha causato lo stato da impostare. Il campo è stato contrassegnato per l'eliminazione di **campi** raccolta dopo il **aggiornamento** metodo viene chiamato.|  
|**adFieldPendingInsert**|0x10000|Indica che il **Append** l'operazione ha causato lo stato da impostare. Il **campo** è stato contrassegnato per essere aggiunto il **campi** raccolta dopo il **aggiornamento** metodo viene chiamato.|  
|**adFieldPendingUnknown**|0x80000|Indica che il provider non è possibile determinare quali lo stato del campo operazione causato da impostare.|  
|**adFieldPendingUnknownDelete**|0x100000|Indica che il provider può determinare l'operazione che ha causato lo stato del campo da impostare e che il campo verrà eliminato dal **campi** raccolta dopo il **aggiornamento** metodo viene chiamato.|  
|**adFieldPermissionDenied**|9|Indica che il campo non può essere modificato perché è definito come di sola lettura.|  
|**adFieldReadOnly**|24|Indica che il campo nell'origine dati viene definito come di sola lettura.|  
|**adFieldResourceExists**|19|Indica che il provider non è riuscito a eseguire l'operazione perché l'URL di destinazione esiste già un oggetto e non è in grado di sovrascrivere l'oggetto.|  
|**adFieldResourceLocked**|18|Indica che il provider non è riuscito a eseguire l'operazione perché l'origine dati è bloccato da uno o più processi o applicazioni.|  
|**adFieldResourceOutOfScope**|25|Indica che un URL di origine o di destinazione è all'esterno dell'ambito del record corrente.|  
|**adFieldSchemaViolation**|11|Indica che il valore viola il vincolo dello schema di origine dati per il campo.|  
|**adFieldSignMismatch**|5|Indica che il valore di dati restituito dal provider è con segno, ma il tipo di dati del valore del campo ADO è senza segno.|  
|**adFieldTruncated**|4|Indica che i dati a lunghezza variabile sono stati troncati durante la lettura dall'origine dati.|  
|**adFieldUnavailable**|8|Indica che il provider non può determinare il valore durante la lettura dall'origine dati. Ad esempio, la riga appena creata, il valore predefinito per la colonna non è disponibile e non fosse ancora stato specificato un nuovo valore.|  
|**adFieldVolumeNotFound**|21|Indica che il provider è in grado di individuare il volume di archiviazione indicato dall'URL.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà Status (campo ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
