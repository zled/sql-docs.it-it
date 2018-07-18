---
title: Proprietà EditMode | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1fd943679fc15cde9a3349b455decc778889b0c6
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277930"
---
# <a name="editmode-property"></a>Proprietà EditMode
Indica lo stato di modifica del record corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) valore.  
  
## <a name="remarks"></a>Remarks  
 ADO gestisce un buffer di modifica associato al record corrente. Questa proprietà indica se sono state apportate modifiche a questo buffer o se è stato creato un nuovo record. Utilizzare il **EditMode** proprietà per determinare lo stato di modifica del record corrente. È possibile verificare le modifiche in sospeso se è stato interrotto un processo di modifica e determinare se è necessario utilizzare il [aggiornamento](../../../ado/reference/ado-api/update-method.md) o [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo.  
  
 In *modalità di aggiornamento immediato* il **EditMode** proprietà verrà reimpostata su **adEditNone** dopo una chiamata per il **aggiornare** metodo viene chiamato . Quando una chiamata a [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md) Elimina correttamente i record nell'origine dati (ad esempio, a causa di violazioni di integrità referenziale), il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) rimane in modalità di modifica (**EditMode** = **adEditInProgress**). Pertanto, **CancelUpdate** deve essere chiamato prima di spostarsi dal record corrente (ad esempio con [spostare](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), o [chiudere](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 In *modalità di aggiornamento batch* (in cui il provider memorizza nella cache più modifiche e li scrive all'origine dati sottostante solo quando si chiama il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) (metodo)), il valore di **EditMode**  proprietà viene modificata quando viene eseguita la prima operazione e non viene ripristinato da una chiamata al **aggiornamento** metodo. Operazioni successive non modificano il valore di **EditMode** proprietà, anche se vengono eseguite diverse operazioni. Ad esempio, se la prima operazione consiste nell'aggiungere un nuovo record, e il secondo apporta modifiche a un oggetto esistente record, la proprietà di **EditMode** saranno ancora **adEditAdd**. Il **EditMode** proprietà non viene reimpostata su **adEditNone** fino a dopo la chiamata a **UpdateBatch**. Per determinare quali operazioni siano state eseguite, impostare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà [adFilterPending](../../../ado/reference/ado-api/filtergroupenum.md) in modo che solo i record con le modifiche in sospeso verranno visibile ed esaminare il [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà di ogni record per determinare le modifiche apportate ai dati.  
  
> [!NOTE]
>  **EditMode** può restituire un valore valido solo se viene rilevato un record corrente. **EditMode** restituirà un errore se [BOF o EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) è true, o se è stato eliminato il record corrente.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [CursorType, LockType ed esempio di proprietà EditMode (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType ed esempio di proprietà EditMode (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [AddNew (metodo) (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Delete (metodo) (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Metodo Update](../../../ado/reference/ado-api/update-method.md)
