---
title: Classe SQLServerXAResource | Documenti Microsoft
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
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bc12b2f49633b00addeec742104d5e525c578f0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverxaresource-class"></a>Classe SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un XAResource XA per la gestione di transazioni distribuite.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.lang.Object  
  
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
  
  
