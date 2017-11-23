---
title: StreamReadEnum | Documenti Microsoft
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
f1_keywords: StreamReadEnum
helpviewer_keywords: StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 875ac187957358e10737b9036ff0feb70da09c54
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="streamreadenum"></a>StreamReadEnum
Specifica se leggere l'intero flusso o la riga successiva in un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Valore predefinito. Legge tutti i byte dal flusso, dalla posizione corrente a partire al [fine del flusso](../../../ado/reference/ado-api/eos-property.md) marcatore. Ciò è valido solo **StreamReadEnum** valore con flussi binari ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeBinary**).|  
|**adReadLine**|-2|Legge la riga successiva dal flusso (definito dal [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Read](../../../ado/reference/ado-api/read-method.md)|[Metodo ReadText](../../../ado/reference/ado-api/readtext-method.md)|
