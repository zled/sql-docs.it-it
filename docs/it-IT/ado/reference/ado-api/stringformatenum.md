---
title: StringFormatEnum | Documenti Microsoft
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
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8cca3873b45fc39eb0df3521ba9ca20941b7cdde
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="stringformatenum"></a>StringFormatEnum
Specifica il formato durante il recupero di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sotto forma di stringa.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Delimita le righe da *RowDelimiter*, le colonne da *ColumnDelimiter*e i valori da null *NullExpr*. Questi tre parametri del [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) metodo sono validi solo con un *StringFormat* di **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
