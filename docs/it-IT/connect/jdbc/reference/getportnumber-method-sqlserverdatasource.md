---
title: Metodo getPortNumber (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8b84c1a9e68deef49103c047ad962bffc9c58b9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getportnumber-method-sqlserverdatasource"></a>Metodo getPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il numero di porta corrente utilizzato per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore che contiene il numero di porta corrente.  
  
## <a name="remarks"></a>Osservazioni  
 Il numero di porta è il numero di porta TCP/IP viene utilizzato quando si apre una connessione socket a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Se la proprietà portNumber non è impostata, il metodo getPortNumber restituisce il valore predefinito 1433.  
  
> [!NOTE]  
>  Il [setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md) metodo non esegue alcun controllo sul valore di porta passato di intervallo. È possibile passare numeri che non sono validi, come 99999, senza generare un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
