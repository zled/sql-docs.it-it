---
title: Metodo updateBytes (int, byte) | Documenti Microsoft
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
- SQLServerResultSet.updateBytes (int, byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 625f48ba-53d0-45a6-8fcb-643f1e0cbe8a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eab6826b353376d07f04cbd170613a37a5ad6449
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatebytes-method-int-byte"></a>Metodo updateBytes (int, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con una matrice di **byte** valori base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBytes(int index,  
                        byte[] x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Matrice di **byte** valori.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateBytes viene specificato dal metodo updateBytes nell'interfaccia Java.SQL. ResultSet.  
  
 In una versione precedente di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], è possibile utilizzare updateBytes per convertire valori tra matrici di byte e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati **data**, **ora**,  **datetime2**, o **datetimeoffset**. In questa versione l'utilizzo del metodo con questi tipi di dati provoca un'eccezione indicante che la conversione non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBytes &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
