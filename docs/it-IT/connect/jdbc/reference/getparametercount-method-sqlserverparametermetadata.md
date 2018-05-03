---
title: Metodo getParameterCount (SQLServerParameterMetaData) | Documenti Microsoft
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
apiname:
- SQLServerParameterMetaData.getParameterCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dbbdacb-74ef-42e7-9bdc-a3229505dad8
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce5d3cdfc8a4f167d67ea6181b5a9e878ad5836d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getparametercount-method-sqlserverparametermetadata"></a>Metodo getParameterCount (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero di parametri di [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto per cui questo [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) oggetto contiene le informazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getParameterCount()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero di parametri.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getParameterCount viene specificato dal metodo getParameterCount nell'interfaccia Java.SQL. parametermetadata.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membri di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
