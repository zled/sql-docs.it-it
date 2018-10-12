---
title: Metodo getObjectInstance (SQLServerDataSourceObjectFactory) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSourceObjectFactory.getObjectInstance
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aab186f41d494e9bddf7885ddf7d9f7b3ff65972
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849506"
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
  
 Valore **Object**.  
  
 *name*  
  
 Nome dell'oggetto .  
  
 *c*  
  
 Contesto relativo al nome specificato.  
  
 *h*  
  
 Ambiente utilizzato nella creazione dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Valore **Object**.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getObjectInstance viene specificato dal metodo getObjectInstance nell'interfaccia ObjectFactory.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [Membri di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Classe SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
