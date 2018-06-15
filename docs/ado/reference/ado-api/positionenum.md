---
title: PositionEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d32d2e507b8ca7214eb142160c65f953771f4527
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280739"
---
# <a name="positionenum"></a>PositionEnum
Specifica la posizione corrente del puntatore del record all'interno di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Indica che il puntatore del record corrente è a inizio file (vale a dire il [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) proprietà **True**).|  
|**adPosEOF**|-3|Indica che il puntatore del record corrente è alla fine del file (vale a dire il [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) proprietà **True**).|  
|**adPosUnknown**|-1|Indica che il **Recordset** è vuoto, la posizione corrente è sconosciuta, o il provider non supporta il [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) o [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) proprietà.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.Position.BOF|  
|AdoEnums.Position.EOF|  
|AdoEnums.Position.UNKNOWN|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Proprietà AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[Proprietà AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
