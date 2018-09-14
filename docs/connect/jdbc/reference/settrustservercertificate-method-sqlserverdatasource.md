---
title: Metodo setTrustServerCertificate (SQLServerDataSource) | Microsoft Docs
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
ms.openlocfilehash: a9883077d2cb947f2c57e54439566f1936badbe5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786304"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Metodo setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un valore **Boolean** che indica se la proprietà trustServerCertificate è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustServerCertificate*  
  
 **true** se il certificato Secure Sockets Layer (SSL) del server deve essere automaticamente considerato attendibile quando il livello di comunicazione è crittografato tramite SSL. In caso contrario, **false**.  
  
## <a name="remarks"></a>Remarks  
 Se la proprietà trustServerCertificate è impostata su **true**, il certificato SSL di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene automaticamente considerato attendibile quando il livello di comunicazione è crittografato tramite SSL. In altri termini, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è **false**.  
  
 Se la proprietà trustServerCertificate è impostata su **false**, il certificato SSL del server viene convalidato da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
