---
title: Metodo deletesAreDetected (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.deletesAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 73f3d994-bbd7-43d2-8b64-50057e278983
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2cae17d96bae15b85dcd9258a0fcb4c45254aa0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deletesaredetected-method-sqlserverdatabasemetadata"></a>Metodo deletesAreDetected (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  È possibile rilevare consente di recuperare o meno di eliminare una riga visibile chiamando il [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean deletesAreDetected(int type)  
```  
  
#### <a name="parameters"></a>Parametri  
 *type*  
  
 Un **int** che indica il set di risultati tipo, che può essere uno dei valori seguenti come definito in Java.SQL. ResultSet o SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Tipi java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Tipi SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Valore restituito  
 **true** se una riga eliminata viene sostituita. **false** se la riga eliminata viene rimossa.  
  
 Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database, questo metodo restituisce **true** per i cursori TYPE_SS_SCROLL_KEYSET e **false** per tutti gli altri risultati del set di tipi.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo deletesAreDetected viene specificato dal metodo deletesAreDetected nell'interfaccia DatabaseMetaData.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] rileva le righe eliminate per tutti i tipi di cursore aggiornabili, anche se il rilevamento è temporaneo per i cursori forward e dinamici.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
