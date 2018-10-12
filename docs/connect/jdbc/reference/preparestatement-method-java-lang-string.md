---
title: Metodo prepareStatement (java.lang.String, int[]) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 72b5c4a5-1382-4b2c-80a0-47c97c5f52d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bec0d56782a7e9cacd236011c79aba2ab2c806a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814489"
---
# <a name="preparestatement-method-javalangstring-int"></a>Metodo prepareStatement (java.lang.String, int[])
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) per l'invio di istruzioni SQL con parametri al database, che è in grado di restituire le chiavi generate automaticamente designate dalla matrice specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int[] columnIndexes)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Valore **String** contenente un'istruzione SQL.  
  
 *columnIndexes*  
  
 Matrice di valori integer.  
  
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
  
  
