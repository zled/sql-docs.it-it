---
title: Metodo getTrustStore (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e23a59adeb94be0f7cacebdc40fb442c3c69f9ae
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="gettruststore-method-sqlserverdatasource"></a>Metodo getTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il percorso (incluso il nome file) del file trustStore del certificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il percorso (incluso il nome di file) del file trustStore del certificato, o null se è impostato alcun valore.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà trustStore non è impostata, il [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) metodo restituisce null.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

