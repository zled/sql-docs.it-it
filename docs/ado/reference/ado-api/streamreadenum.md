---
title: StreamReadEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26ccabf3e73a67c14e7201f26e4ebf739a6352cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644646"
---
# <a name="streamreadenum"></a>StreamReadEnum
Specifica se l'intero flusso o nella riga successiva deve essere letti da un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Valore predefinito. Legge e versioni successive a tutti i byte dal flusso, dalla posizione corrente di [EOS](../../../ado/reference/ado-api/eos-property.md) marcatore. Ciò è valido solo **StreamReadEnum** valore con flussi binari ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) viene **adTypeBinary**).|  
|**adReadLine**|-2|Legge la riga successiva dal flusso (definito dal [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà).|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Queste costanti non dispongono di equivalenti di ADO o WFC.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Read](../../../ado/reference/ado-api/read-method.md)|[Metodo ReadText](../../../ado/reference/ado-api/readtext-method.md)|
