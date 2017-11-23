---
title: "Proprietà CursorType (ADO) | Documenti Microsoft"
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
f1_keywords: Recordset15::CursorType
helpviewer_keywords: CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f1f16755e5030cec19d7b513f725f3fd5defb3f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="cursortype-property-ado"></a>Proprietà CursorType (ADO)
Indica il tipo di cursore utilizzato in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) valore. Il valore predefinito è **adOpenForwardOnly**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CursorType** proprietà per specificare il tipo di cursore che deve essere utilizzato quando si apre il **Recordset** oggetto.  
  
 Solo l'impostazione **adOpenStatic** è supportato se il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient**. Se è impostato un valore non supportato, verrà restituito alcun errore; è supportato il più vicino **CursorType** verrà utilizzato.  
  
 Se un provider non supporta il tipo di cursore richiesto, può restituire un altro tipo di cursore. Il **CursorType** proprietà verrà modificata per corrispondere al tipo di cursore effettivo in uso quando il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto è aperto. Per verificare le funzionalità specifiche del cursore restituito, utilizzare il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo. Dopo aver chiuso la **Recordset**, **CursorType** proprietà viene ripristinata l'impostazione originale.  
  
 Il grafico seguente illustra la funzionalità del provider (identificato da **supporta** costanti del metodo) necessaria per ogni tipo di cursore.  
  
|Per un oggetto Recordset di questo CursorType|Il metodo supporta deve restituire True per tutte le costanti|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|none|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**Impostare**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Sebbene **supporta**(**adUpdateBatch**) può essere true per i cursori dinamici e forward-only, per gli aggiornamenti batch deve utilizzare un cursore statico o keyset. Impostare il [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) proprietà **adLockBatchOptimistic** e **CursorLocation** proprietà **adUseClient** per abilitare il cursore Servizio per OLE DB, che è necessario per gli aggiornamenti batch.  
  
 Il **CursorType** proprietà è di lettura/scrittura quando il **Recordset** è chiuso e di sola lettura quando è aperto.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando utilizzato sul lato client **Recordset** oggetto, il **CursorType** proprietà può essere impostata solo su **adOpenStatic**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [CursorType, LockType ed esempio di proprietà EditMode (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType ed esempio di proprietà EditMode (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Metodo Supports](../../../ado/reference/ado-api/supports-method.md)
