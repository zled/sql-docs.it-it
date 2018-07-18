---
title: Metodo (lang) addBatch | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.addBatch (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 093f6c3b-49a6-4043-9993-bd0482de04dd
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4dde1fd65758a3aec96bb9edb0455a290a0bcc5a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32829156"
---
# <a name="addbatch-method-javalangstring"></a>Metodo addBatch (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiunge il comando SQL specificato all'elenco corrente dei comandi per questo [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo addBatch viene specificato dal metodo addBatch nell'interfaccia Java.SQL. Statement.  
  
 Chiamare questo metodo comporterà un'eccezione poiché l'istruzione SQL per l'oggetto SQLServerPreparedStatement non viene specificato quando viene creato l'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo addBatch &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
