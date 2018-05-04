---
title: Metodo getTrustServerCertificate (SQLServerDataSource) | Documenti Microsoft
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
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0d22963fc8e916bb554ba5bb385efe1abfcd84c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>Metodo getTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un **booleano** valore che indica se la proprietà trustServerCertificate è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se trustServerCertificate è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà trustServerCertificate è impostata su **true**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato Secure Sockets Layer (SSL) viene automaticamente considerato attendibile quando il livello di comunicazione è crittografato tramite SSL. In altre parole, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non convaliderà il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL. Il valore predefinito è **false**.  
  
 Se la proprietà trustServerCertificate è impostata su **false**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convaliderà il certificato SSL del server.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
