---
title: Metodo GetChildren (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f385753f2e9dee3d99e4a6b41891ef69f4b70c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getchildren-method-ado"></a>Metodo GetChildren (ADO)
Restituisce un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) le cui righe rappresentano gli elementi figlio di una raccolta [Record](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **Recordset** oggetto per cui ogni riga rappresenta un elemento figlio dell'oggetto corrente **Record** oggetto. Ad esempio, gli elementi figlio di un **Record** che rappresenta una directory saranno i file e sottodirectory contenute all'interno della directory padre.  
  
## <a name="remarks"></a>Osservazioni  
 Il provider determina quali colonne sono presenti nell'oggetto restituito **Recordset**. Un provider di origine del documento, ad esempio, restituisce sempre una risorsa **Recordset**.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
