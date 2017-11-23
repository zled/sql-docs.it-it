---
title: Metodo getObjectInstance (SQLServerDataSourceObjectFactory) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSourceObjectFactory.getObjectInstance
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa9417d9b20ae5c1858c3c8f10019383565c4330
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getobjectinstance-method-sqlserverdatasourceobjectfactory"></a>Metodo getObjectInstance (SQLServerDataSourceObjectFactory)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un'istanza dell'oggetto origine dati specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.Object getObjectInstance(java.lang.Object ref,  
                                          javax.naming.Name name,  
                                          javax.naming.Context c,  
                                          java.util.Hashtable h)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ref*  
  
 Un **oggetto** valore.  
  
 *name*  
  
 Nome dell'oggetto .  
  
 *c*  
  
 Contesto relativo al nome specificato.  
  
 *h*  
  
 Ambiente utilizzato nella creazione dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Un **oggetto** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getObjectInstance viene specificato dal metodo getObjectInstance nell'interfaccia javax.naming.spi. ObjectFactory.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [Membri di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Classe SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
