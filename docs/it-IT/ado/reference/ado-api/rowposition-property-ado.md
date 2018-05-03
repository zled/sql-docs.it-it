---
title: Proprietà RowPosition (ADO) | Documenti Microsoft
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
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce1861d78db74a92831fd133c9f5a7a7c77aa3ae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rowposition-property-ado"></a>Proprietà RowPosition (ADO)
Ottiene o imposta OLE DB **RowPosition** oggetto da/su un **ADORecordsetConstruction** oggetto. Quando si utilizza **put_RowPosition** per impostare il **RowPosition** oggetto, il valore risultante **Recordset** viene utilizzata da object il **RowPosition** oggetto determinare la riga corrente.  
  
 Proprietà di lettura/scrittura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Parametri  
 *ppRowPos*  
 Puntatore a OLE DB **RowPosition** oggetto.  
  
 *PRowPos*  
 OLE DB **RowPosition** oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Metodo di questa proprietà restituisce i valori HRESULT standard, inclusi S_OK ed E_FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Quando questa proprietà è impostata, se il **set di righe** oggetto di **RowPosition** oggetto è diverso dal **set di righe** oggetto di **Recordset**dell'oggetto, il primo sostituisce quest'ultimo. Lo stesso comportamento si applica all'oggetto corrente **capitolo** del **RowPosition** anche.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
