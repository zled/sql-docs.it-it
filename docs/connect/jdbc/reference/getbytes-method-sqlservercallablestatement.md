---
title: Metodo getBytes (SQLServerCallableStatement) | Documenti Microsoft
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
- SQLServerCallableStatement.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6e88cea-54b3-4d18-a9af-db54abf19f45
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8acb32814e0d2fff0778aa72e5b619f8fbf3c7e4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830256"
---
# <a name="getbytes-method-sqlservercallablestatement"></a>Metodo getBytes (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come matrice di byte.  
  
## <a name="overload-list"></a>Elenco degli overload  
  
|Nome|Description|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int.md)|Recupera il valore del parametro designato come matrice di valori byte in base all'indice del parametro.|  
|[getBytes (lang)](../../../connect/jdbc/reference/getbytes-method-java-lang-string.md)|Recupera il valore del parametro designato come matrice di valori byte in base al nome del parametro.|  
  
## <a name="remarks"></a>Osservazioni  
 In una versione precedente del [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], è possibile utilizzare Sqlservercallablestatement per convertire valori tra matrici di byte e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati **data**, **ora**, **datetime2**, o **datetimeoffset**. In questa versione l'utilizzo del metodo con questi tipi di dati provoca un'eccezione indicante che la conversione non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
