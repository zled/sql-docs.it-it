---
title: ConnectOptionEnum | Documenti Microsoft
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
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c3a974a46acd32a75773f7bd5034f30a62152499
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Specifica se il [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo di un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto deve restituire una volta stabilita la connessione (in modo sincrono) o prima (in modo asincrono).  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Apre la connessione in modo asincrono. Il [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) evento può essere utilizzato per determinare quando la connessione è disponibile.|  
|**adConnectUnspecified**|-1|Valore predefinito. Apre la connessione in modo sincrono.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Open (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
