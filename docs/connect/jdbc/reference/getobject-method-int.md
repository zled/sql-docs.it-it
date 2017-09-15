---
title: Metodo getObject (int) | Documenti Microsoft
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
- SQLServerCallableStatement.getObject (jnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4b8366b-c065-48e1-b712-19e2d9834228
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4e43c9e04aefe5b0c658ab41112cfdf764454291
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getobject-method-int"></a>Metodo getObject (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come oggetto nel linguaggio di programmazione Java in base all'indice del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.Object getObject(int index)  
```  
  
#### <a name="parameters"></a>Parametri  
 *indice*  
  
 Un **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Un **oggetto** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getObject viene specificato dal metodo getObject nell'interfaccia Java.SQL. CallableStatement.  
  
 Il metodo restituirà il valore della colonna specificata come oggetto Java. Il tipo dell'oggetto Java sarà il tipo di oggetto Java predefinito che corrisponde al tipo SQL della colonna, in base al mapping per i tipi predefiniti indicato nella specifica JDBC. Se si tratta di un valore NULL SQL, il driver restituisce un valore Null Java.  
  
 Questo metodo può essere utilizzato anche per leggere tipi di dati astratti specifici del database. In JDBC 2.0 il comportamento del metodo getObject è stato esteso per materializzare i dati di tipi SQL definiti dall'utente. Quando una colonna contiene un valore di tipo structured o distinct, il comportamento di questo metodo è come se fosse una chiamata a `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 A partire dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0 per:  
  
-   Un valore di tipo **data** verrà restituito come oggetto java.SQL. date.  
  
-   Un valore di tipo **ora** verrà restituito come oggetto java.SQL.  
  
-   Un valore di tipo **datetime2** sarà restituito come oggetto java.SQL. timestamp.  
  
-   Un valore di tipo **datetimeoffset** verrà restituito come oggetto Microsoft.SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getObject &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
