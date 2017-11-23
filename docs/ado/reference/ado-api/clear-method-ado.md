---
title: Clear (metodo) (ADO) | Documenti Microsoft
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
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords: Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e1770a8bbf9fac82dece435a46374876b55d1c14
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="clear-method-ado"></a>Clear (metodo) (ADO)
Rimuove tutti i [errore](../../../ado/reference/ado-api/error-object.md) oggetti dal [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **deselezionare** metodo il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme per rimuovere tutte le [errore](../../../ado/reference/ado-api/error-object.md) oggetti dalla raccolta. Quando si verifica un errore, ADO Cancella automaticamente il **errori** insieme e vi inserisce con **errore** oggetti in base al nuovo errore.  
  
 Alcune proprietà e metodi restituiscono avvisi che vengono visualizzati come **errore** gli oggetti di **errori** raccolta ma non arrestano l'esecuzione del programma. Prima di chiamare il [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodi su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto; il [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo su un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) ; dell'oggetto o impostare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà in un **Recordset** dell'oggetto, chiamare il **deselezionare**metodo il **errori** insieme. In questo modo, è possibile leggere il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà del **errori** raccolta da testare per avvisi restituiti.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Execute, Requery e deselezionare l'esempio di metodi (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery e Clear metodi esempio (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery e deselezionare l'esempio di metodi (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Metodo Delete (insieme Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Metodo Delete (insieme Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete (metodo) (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Proprietà filtro](../../../ado/reference/ado-api/filter-property.md)   
 [Risincronizzazione (metodo)](../../../ado/reference/ado-api/resync-method.md)   
 [Metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
