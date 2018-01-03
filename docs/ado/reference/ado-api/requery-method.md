---
title: Requery (metodo) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords: Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90ca81710f2c20929305e894fe2dbda49bb5b3b8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="requery-method"></a>Requery (metodo)
Aggiorna i dati in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto rieseguendo la query in cui si basa l'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Parametri  
 *Opzioni*  
 Facoltativo. Maschera di bit che contiene [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) e [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valori che influenzano l'operazione.  
  
> [!NOTE]
>  Se *opzioni* è impostato su **adAsyncExecute**, l'operazione verrà eseguita in modo asincrono e un [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) verrà generato l'evento quando conclude. Il **ExecuteOpenEnum** valori di **adExecuteStream** o **adExecuteStream** non deve essere utilizzato con **Requery**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **Requery** per aggiornare l'intero contenuto di un **Recordset** oggetto dall'origine dati rieseguendo il comando originale e recuperando i dati una seconda volta. Chiamare questo metodo è equivalente alla chiamata di [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) e [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodi in successione. Se si modifica il record corrente o aggiungendo un nuovo record, si verifica un errore.  
  
 Mentre il **Recordset** oggetto è aperto, le proprietà che definiscono la natura del cursore ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md) e così via) sono di sola lettura. Di conseguenza, il **Requery** metodo può aggiornare solo il cursore corrente. Per modificare le proprietà del cursore e visualizzare i risultati, è necessario utilizzare il [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodo in modo che le proprietà di lettura/scrittura nuovamente. È quindi possibile modificare le impostazioni di proprietà e una chiamata di [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo per riaprire il cursore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Execute, Requery e deselezionare l'esempio di metodi (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery e Clear metodi esempio (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery e deselezionare l'esempio di metodi (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
