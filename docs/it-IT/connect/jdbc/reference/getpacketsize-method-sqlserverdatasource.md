---
title: Metodo getPacketSize (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a320d10b6dab2335226087f97d54edc213d4b50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>Metodo getPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce le dimensioni di pacchetto di rete corrente utilizzata per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], specificato in byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore contenente le dimensioni di pacchetto di rete corrente.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà packetSize non è impostata, il metodo getPacketSize restituisce il valore predefinito di 8000.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
