---
title: Proprietà Status (Recordset ADO) | Documenti Microsoft
ms.prod: sql
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
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1a3c09b9613c2fe9bd84ea921aef8a3e09a14b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="status-property-ado-recordset"></a>Proprietà Status (Recordset ADO)
Indica lo stato del record corrente rispetto all'aggiornamento batch o altre operazioni bulk.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce la somma di uno o più [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) valori.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **stato** proprietà per individuare le modifiche in sospeso per i record modificati durante l'aggiornamento in batch. È inoltre possibile utilizzare il **stato** proprietà per visualizzare lo stato del record con esito negativo durante le operazioni bulk, ad esempio quando si chiama il [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodi su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto o impostare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà in un **Recordset** oggetto in una matrice di segnalibri. Questa proprietà, è possibile determinare come un record specificato non è riuscita e risolverlo di conseguenza.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Status (Recordset) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Esempio di proprietà Status (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
