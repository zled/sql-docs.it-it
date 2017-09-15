---
title: "Proprietà ParentRow (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 52b23aa90e3a2e0998547849d71c3c10a3e0552d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="parentrow-property-ado"></a>Proprietà ParentRow (ADO)
Imposta il contenitore di OLE DB **riga** oggetto un **ADORecordConstruction** oggetto, in modo che l'elemento padre della riga viene trasformato in un oggetto ADO **Record** oggetto.  
  
 Sola scrittura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Parametri  
 *pParent*  
 Un contenitore di una riga.  
  
## <a name="return-values"></a>Valori restituiti  
 Metodo di questa proprietà restituisce i valori HRESULT standard, inclusi S_OK ed E_FAIL.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
