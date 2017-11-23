---
title: Metodo registerOutParameter (int, int, int) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerCallableStatement.registerOutParameter (int, int, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: d902d4e0-881f-4182-814c-0ede9a8da7fd
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d59b50e1f5ad220a40bad10fdeb203571382cec
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="registeroutparameter-method-int-int-int"></a>Metodo registerOutParameter (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registra il parametro OUT nella posizione ordinale specificata nel tipo e nella scala JDBC specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType,  
                                 int scale)  
```  
  
#### <a name="parameters"></a>Parametri  
 *indice*  
  
 Un **int** che indica la posizione ordinale del parametro.  
  
 *sqlType*  
  
 Codice di tipo JDBC come definito in java.sql.Types.  
  
 *scala*  
  
 Un **int** che indica il numero di cifre da posizionare a destra del separatore decimale.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo registerOutParameter viene specificato dal metodo registerOutParameter nell'interfaccia Java.SQL. CallableStatement.  
  
 A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0, quando *sqlType* è di tipo java.sql.Types.TIME, il comportamento di questo metodo viene modificato dal **sendTimeAsDatetime** proprietà di connessione ([Impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md)) e [Setsendtimeasdatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Per ulteriori informazioni, vedere [Java.SQL configurazione come i valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo registerOutParameter &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
