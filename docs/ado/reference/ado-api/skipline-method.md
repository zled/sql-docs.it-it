---
title: Metodo SkipLine | Documenti Microsoft
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
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a24691a7579efd5585ccecf413158273354152cd
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="skipline-method"></a>Metodo SkipLine
Ignora un'intera riga durante la lettura di un testo [flusso](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Osservazioni  
 Tutti i caratteri, incluso il separatore di riga successivo verranno ignorati. Per impostazione predefinita, il [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) è **adCRLF**. Se si tenta di superare [fine del flusso](../../../ado/reference/ado-api/eos-property.md), verrà mantenuta la posizione corrente **fine del flusso**.  
  
 Il **SkipLine** metodo viene utilizzato con flussi di testo ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
