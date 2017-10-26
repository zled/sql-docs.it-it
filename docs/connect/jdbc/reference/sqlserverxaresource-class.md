---
title: Classe SQLServerXAResource | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c5e0cb02544e0ea96c29758f7c50179de48cf7a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaresource-class"></a>Classe SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un XAResource XA per la gestione di transazioni distribuite.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** lang  
  
 **Implementa:** XAResource  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Osservazioni  
 Le transazioni XA vengono implementate [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizzando [!INCLUDE[msCoName](../../../includes/msconame_md.md)] gestione transazioni distribuite (DTC). La classe SQLServerXAResource effettua chiamate a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] estesi dll denominata sqljdbc_xa.dll che si interfaccia con DTC. Le chiamate XA ricevute dal SQLServerXAResource (XA_START, XA_END, XA_PREPARE e così via) vengono mappate alle chiamate corrispondenti alle funzioni DTC.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

