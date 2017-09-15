---
title: I membri di SQLServerParameterMetaData | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9ebb203-2013-4feb-94f5-494b7f098f9a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6fbc42820d6a35c054f705eefec36a9c05ee08c3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverparametermetadata-members"></a>Membri di SQLServerParameterMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 nessuna.  
  
## <a name="fields"></a>Campi  
 nessuna.  
  
## <a name="inherited-fields"></a>Campi ereditati  
  
|Nome|Description|  
|----------|-----------------|  
|java.sql.ParameterMetaData|parameterModeIn, parameterModeInOut, parameterModeOut, parameterModeUnknown, parameterNoNulls, parameterNullable, parameterNullableUnknown|  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[getParameterClassName](../../../connect/jdbc/reference/getparameterclassname-method-sqlserverparametermetadata.md)|Recupera il nome completo della classe Java le cui istanze devono essere passate al [setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) metodo il [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.|  
|[getParameterCount](../../../connect/jdbc/reference/getparametercount-method-sqlserverparametermetadata.md)|Recupera il numero di parametri di [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto per cui questo [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) oggetto contiene le informazioni.|  
|[getParameterMode](../../../connect/jdbc/reference/getparametermode-method-sqlserverparametermetadata.md)|Recupera la modalità del parametro designato.|  
|[getParameterType](../../../connect/jdbc/reference/getparametertype-method-sqlserverparametermetadata.md)|Recupera il tipo SQL del parametro designato.|  
|[getParameterTypeName](../../../connect/jdbc/reference/getparametertypename-method-sqlserverparametermetadata.md)|Recupera il nome del tipo specifico del database del parametro designato.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverparametermetadata.md)|Recupera il numero di cifre decimali per il parametro designato.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverparametermetadata.md)|Recupera il numero di cifre a destra del separatore decimale per il parametro designato.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverparametermetadata.md)|Recupera un valore che indica se nel parametro designato sono consentiti valori Null.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverparametermetadata.md)|Recupera un valore che indica se i valori per il parametro designato possono essere numeri con segno.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
