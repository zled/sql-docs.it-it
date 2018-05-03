---
title: getBytes, metodo (lang) | Documenti Microsoft
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
- SQLServerCallableStatement.getBytes (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4d0dac7f-7f39-47a2-953e-80ab03688d82
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1aa1cd78801599e459cb6217c74ba33da18b504b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getbytes-method-javalangstring"></a>Metodo getBytes (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come matrice di valori byte in base al nome del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public byte[] getBytes(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Matrice di **byte** valori.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 In una versione precedente di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], è possibile utilizzare Sqlservercallablestatement per convertire valori tra matrici di byte e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati **data**, **ora**,  **datetime2**, o **datetimeoffset**. In questa versione l'utilizzo del metodo con questi tipi di dati provoca un'eccezione indicante che la conversione non è supportata.  
  
 Questo metodo getBytes viene specificato dal metodo getBytes nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBytes &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
