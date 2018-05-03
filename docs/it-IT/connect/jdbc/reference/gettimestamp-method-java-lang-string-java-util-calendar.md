---
title: Metodo getTimestamp (lang, java.util.Calendar) | Documenti Microsoft
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
- SQLServerCallableStatement.getTimestamp (java.lang.String,java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 770668d9-2e52-4ff0-be2f-ebf78fd41644
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 310374294313d7eca6ea3aa8e821254e07b67d27
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettimestamp-method-javalangstring-javautilcalendar"></a>Metodo getTimestamp (java.lang.String, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come oggetto java.SQL. timestamp nel linguaggio di programmazione Java, dato il nome del parametro, utilizzando un oggetto di calendario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String name,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parametri  
 *name*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *licenza CAL*  
  
 Un oggetto di calendario.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di tipo Timestamp.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTimestamp viene specificato dal metodo getTimestamp nell'interfaccia Java.SQL. CallableStatement.  
  
 Questo metodo restituisce valori solo dalle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** e **smalldatetime** colonne.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getTimestamp &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
