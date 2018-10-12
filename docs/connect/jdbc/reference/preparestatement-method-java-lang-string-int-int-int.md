---
title: Metodo prepareStatement (java.lang.String, int, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b78d2192-f315-4c45-9051-c77059e2c3f4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b3979628c2676b6a3780536a217885e8547d42e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764769"
---
# <a name="preparestatement-method-javalangstring-int-int-int"></a>Metodo prepareStatement (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) che genera oggetti [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) con il tipo, la concorrenza e la trattenibilità specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int nType,  
                                                   int nConcur,  
                                                   int nHold)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Valore **String** contenente un'istruzione SQL.  
  
 *NLE*  
  
 Valore **int** che indica il tipo di set di risultati.  
  
 *nConcur*  
  
 Valore **int** che indica il tipo di concorrenza del set di risultati.  
  
 *nHold*  
  
 Valore **int** che indica la trattenibilità dei set di risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di impostazione PreparedStatement.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo prepareStatement viene specificato dal metodo prepareStatement nell'interfaccia Java.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo prepareStatement &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
