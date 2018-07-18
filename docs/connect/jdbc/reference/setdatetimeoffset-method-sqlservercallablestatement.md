---
title: Metodo setDateTimeOffset (SQLServerCallableStatement) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb5ed787351a9159f9eb839575743a4137cdafea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841616"
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>Metodo setDateTimeOffset (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 Imposta il valore della colonna specificata per il [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Nome di una colonna.  
  
 *t*  
  
 Il [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile recuperare un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore con [Getdatetimeoffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md).  
  
 [setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) accetta il numero ordinale della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
