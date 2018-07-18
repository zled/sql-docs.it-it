---
title: Metodo getUser (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7cd095dc3968ae89dfedb110cc5a75eb1b19844a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839236"
---
# <a name="getuser-method-sqlserverdatasource"></a>Metodo getUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome utente utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome utente.  
  
## <a name="remarks"></a>Osservazioni  
 Il [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) metodo imposta il nome utente da utilizzare quando ci si connette all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Se il valore del nome utente non è impostato, il metodo getUser restituisce il valore predefinito Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
