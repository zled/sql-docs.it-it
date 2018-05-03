---
title: Proprietà NamedParameters (ADO) | Documenti Microsoft
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
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c64c7ee4bf239ca3084417724209ad715d63eeda
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="namedparameters-property-ado"></a>Proprietà NamedParameters (ADO)
Indica se i nomi di parametro devono essere passati al provider.  
  
## <a name="remarks"></a>Osservazioni  
 Quando questa proprietà è true, ADO passa il valore del **nome** proprietà di ogni parametro nella **parametro** raccolta per il [oggetto comando](../../../ado/reference/ado-api/command-object-ado.md). Il provider utilizza un nome di parametro per devono corrispondere a quelli di **CommandText** o **CommandStream** proprietà. Se questa proprietà è false (impostazione predefinita), i nomi dei parametri vengono ignorati e il provider utilizza l'ordine dei parametri per confrontare valori ai parametri di **CommandText** o **CommandStream** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Proprietà CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
