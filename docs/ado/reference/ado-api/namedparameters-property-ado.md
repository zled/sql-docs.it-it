---
title: Proprietà NamedParameters (ADO) | Documenti Microsoft
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
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d66b740bbe042510de019571639e796787caaf42
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279630"
---
# <a name="namedparameters-property-ado"></a>Proprietà NamedParameters (ADO)
Indica se i nomi di parametro devono essere passati al provider.  
  
## <a name="remarks"></a>Remarks  
 Quando questa proprietà è true, ADO passa il valore del **nome** proprietà di ogni parametro nella **parametro** raccolta per il [oggetto comando](../../../ado/reference/ado-api/command-object-ado.md). Il provider utilizza un nome di parametro per devono corrispondere a quelli di **CommandText** o **CommandStream** proprietà. Se questa proprietà è false (impostazione predefinita), i nomi dei parametri vengono ignorati e il provider utilizza l'ordine dei parametri per confrontare valori ai parametri di **CommandText** o **CommandStream** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Proprietà CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
