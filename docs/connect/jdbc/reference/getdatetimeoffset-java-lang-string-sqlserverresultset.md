---
title: getDateTimeOffset(java.lang.string) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e585927c-0dee-43fd-b71e-c9f1701790bd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d1222e85f3a35c79bff9d2d78f3d96507162047
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645459"
---
# <a name="getdatetimeoffsetjavalangstring-sqlserverresultset"></a>getDateTimeOffset(java.lang.string) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] JDBC Driver 3.0 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Recupera il valore della colonna designata come oggetto [DateTimeOffset Class](../../../connect/jdbc/reference/datetimeoffset-class.md) nel linguaggio di programmazione Java in base all'indice del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(String columnName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 È possibile aggiornare una [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore con [Updatedatetimeoffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
