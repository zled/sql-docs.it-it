---
title: Costruttore SQLServerClob (SQLServerConnection, lang) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 028d7d4803ff53f518067d869fa192512209d723
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>Costruttore SQLServerClob (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inizializza una nuova istanza di [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md) classe quando viene specificato un [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto e una stringa di dati.  
  
> [!NOTE]  
>  Questo metodo è deprecato nella versione 2.0 del driver JDBC. Utilizzare invece il [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Parametri  
 *connessione*  
  
 Oggetto SQLServerConnection.  
  
 *dati*  
  
 I dati CLOB.  
  
## <a name="see-also"></a>Vedere anche  
 [Costruttori di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
