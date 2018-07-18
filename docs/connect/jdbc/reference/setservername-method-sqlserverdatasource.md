---
title: Metodo setServerName (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8843d601229fc8db7e374857857841eb5e3fc52a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844806"
---
# <a name="setservername-method-sqlserverdatasource"></a>Metodo setServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ServerName*  
  
 Oggetto **stringa** che contiene il nome del server.  
  
## <a name="remarks"></a>Osservazioni  
 Il nome del server è il nome host del computer di destinazione che esegue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Se la proprietà serverName non è impostata, [getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) restituisce il valore predefinito null.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
