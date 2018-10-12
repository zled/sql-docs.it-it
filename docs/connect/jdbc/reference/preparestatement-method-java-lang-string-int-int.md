---
title: Metodo prepareStatement (java.lang.String, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95c3f823e230a51ada0f966c68a71b189eb482d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812389"
---
# <a name="preparestatement-method-javalangstring-int-int"></a>Metodo prepareStatement (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) che genera oggetti [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) con il tipo e la concorrenza specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Crediti*  
  
 Valore **String** contenente un'istruzione SQL.  
  
 *resultSetType*  
  
 Valore **int** che indica il tipo di set di risultati.  
  
 *resultSetConcurrency*  
  
 Valore **int** che indica il tipo di concorrenza del set di risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di impostazione PreparedStatement.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo prepareStatement viene specificato dal metodo prepareStatement nell'interfaccia Java.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
