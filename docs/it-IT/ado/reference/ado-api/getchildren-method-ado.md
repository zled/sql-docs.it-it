---
title: Metodo GetChildren (ADO) | Documenti Microsoft
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
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 170f17c66ea05a3df7dc6135918d164bd66f993e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
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
