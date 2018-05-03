---
title: setAuthenticationScheme (SQLServerDataSource) | Documenti Microsoft
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
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 249bfe5e0e3eff2171c1c8508129ff9f2f0f38fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setauthenticationscheme-sqlserverdatasource"></a>setAuthenticationScheme (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica il tipo di sicurezza integrata che si desidera venga utilizzata dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
public void setAuthenticationScheme(String authenticationScheme);  
```  
  
#### <a name="parameters"></a>Parametri  
 *AuthenticationScheme*  
  
 I valori sono **"JavaKerberos"** e il valore predefinito **"NativeAuthentication"**. Per ulteriori informazioni, vedere [utilizzando l'autenticazione integrata Kerberos per connettersi a SQL Server](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
