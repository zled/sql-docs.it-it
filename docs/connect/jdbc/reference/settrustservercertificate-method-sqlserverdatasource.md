---
title: Metodo setTrustServerCertificate (SQLServerDataSource) | Documenti Microsoft
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
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb5923c3078944a446abfc763c76122f44af2396
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845706"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Metodo setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un **booleano** valore che indica se la proprietà trustServerCertificate è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *TrustServerCertificate*  
  
 **true** se il certificato Secure Sockets Layer (SSL) del server deve essere considerato automaticamente attendibile quando il livello di comunicazione è crittografato tramite SSL. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà trustServerCertificate è impostata su **true**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL viene automaticamente considerato attendibile quando il livello di comunicazione viene crittografato mediante SSL. In altre parole, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non convaliderà il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL. Il valore predefinito è **false**.  
  
 Se la proprietà trustServerCertificate è impostata su **false**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convaliderà il certificato SSL del server.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
