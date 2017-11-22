---
title: "Proprietà capitolo (ADO) | Documenti Microsoft"
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
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords: Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 026fc2e66f9dca3243791f3cd2c1e984f13087d8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="chapter-property-ado"></a>Proprietà capitolo (ADO)
Ottiene o imposta OLE DB **capitolo** oggetto da/su un [interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) oggetto. Quando si utilizza **put_Chapter** per impostare il **capitolo** dell'oggetto, un subset di righe viene trasformato in un oggetto ADO [oggetto Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Imposta il capitolo corrente del **set di righe**oggetto. Si tratta di una proprietà di lettura/scrittura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Parametri  
 *plChapter*  
 Puntatore all'handle del capitolo.  
  
 *LChapter*  
 Handle del capitolo.  
  
## <a name="return-values"></a>Valori restituiti  
 Metodo di questa proprietà restituisce i valori HRESULT standard, inclusi S_OK ed E_FAIL.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
