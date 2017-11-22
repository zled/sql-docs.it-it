---
title: "Proprietà set di righe (ADO) | Documenti Microsoft"
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
- ADORecordsetConstruction::PutRowset
- ADORecordsetConstruction::GetRowset
- ADORecordsetConstruction::Rowset
- ADORecordsetConstruction::put_Rowset
- ADORecordsetConstruction::get_Rowset
helpviewer_keywords: Rowset property [ADO]
ms.assetid: 7d359294-4ff2-47e0-8111-0c221b24d80e
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8792f0b78e2dcc565d88847767506c310160ed5c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="rowset-property-ado"></a>Proprietà set di righe (ADO)
Ottiene o imposta OLE DB **set di righe** oggetto da/su un **ADORecordsetConstruction** oggetto. Quando si utilizza put_Rowset, il set di righe viene convertito in un oggetto ADO **Recordset** oggetto.  
  
 Proprietà di lettura/scrittura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT get_Rowset([out, retval] IUnknown** ppRowset);  
HRESULT put_Rowset([in] IUnknown* pRowset);  
```  
  
## <a name="parameters"></a>Parametri  
 *ppRowset*  
 Puntatore a OLE DB **set di righe** oggetto.  
  
 *PRowset*  
 OLE DB **set di righe** oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Metodo di questa proprietà restituisce i valori HRESULT standard, inclusi S_OK ed E_FAIL.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
