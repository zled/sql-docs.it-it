---
title: Metodo setString (SQLServerCallableStatement) | Documenti Microsoft
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
apiname: SQLServerCallableStatement.setString
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb2a0b29e765c2160e4fa21e78f6b19a707a9c0b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="setstring-method-sqlservercallablestatement"></a>Metodo setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per il linguaggio specificato **stringa** valore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *s*  
  
 Oggetto **stringa** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setString viene specificato dal metodo setString nell'interfaccia Java.SQL. CallableStatement.  
  
 Stringa binarie conversioni vengono eseguite solo quando [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] conosce il tipo di destinazione è binario. In casi in cui il driver JDBC non è noto il tipo sottostante, passerà il **stringa** letterale e viene restituito un errore del server se il server non è possibile eseguire la conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
