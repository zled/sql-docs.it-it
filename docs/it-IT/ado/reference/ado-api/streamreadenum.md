---
title: StreamReadEnum | Documenti Microsoft
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
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9043d6ed09aff812bb9f5ae352ac32517a0894d7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="streamreadenum"></a>StreamReadEnum
Specifica se leggere l'intero flusso o la riga successiva in un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Valore predefinito. Legge tutti i byte dal flusso, dalla posizione corrente a partire al [fine del flusso](../../../ado/reference/ado-api/eos-property.md) marcatore. Ciò è valido solo **StreamReadEnum** valore con flussi binari ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeBinary**).|  
|**adReadLine**|-2|Legge la riga successiva dal flusso (definito dal [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Read](../../../ado/reference/ado-api/read-method.md)|[Metodo ReadText](../../../ado/reference/ado-api/readtext-method.md)|
