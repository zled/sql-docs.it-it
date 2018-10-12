---
title: Metodo getInt (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getInt (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c465ff91-ab96-41de-8917-96c4974c2624
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3d6aa0a75a519da0399d46a2c9caa24566ef673
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766619"
---
# <a name="getint-method-int-sqlserverresultset"></a>Metodo getInt (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore dell'indice di colonna designata nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come **int** nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getInt(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Valore **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un' **int** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getInt viene specificato dal metodo getInt nell'interfaccia java.sql.ResultSet.  
  
 Questo metodo è supportato solo sui tipi di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che possono restituire in modo sicuro un valore integer, ad esempio int, smallint, tinyint e bit. L'utilizzo di questo metodo su qualsiasi altro tipo di dati genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getInt &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
