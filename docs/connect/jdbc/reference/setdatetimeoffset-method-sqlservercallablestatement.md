---
title: Metodo setDateTimeOffset (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e739eb92c3c4b35d65399ad5665b42445e9df00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764715"
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>Metodo setDateTimeOffset (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] JDBC Driver 3.0 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
  
## <a name="remarks"></a>Remarks  
 È possibile recuperare un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore con [Getdatetimeoffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md).  
  
 [setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) accetta il numero ordinale della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
