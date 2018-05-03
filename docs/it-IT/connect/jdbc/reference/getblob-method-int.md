---
title: Metodo getBlob (int) | Documenti Microsoft
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
- SQLServerCallableStatement.getBlob (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bef3ef12-cdda-4a18-90d6-4a501b8e30f0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 881c180e1d7a316cf6e774528b0f277dff3acdf6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getblob-method-int"></a>Metodo getBlob (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro BLOB JDBC designato come oggetto Blob nel linguaggio di programmazione Java specificato all'indice del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Blob getBlob(int index)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto Blob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBlob viene specificato dal metodo getBlob nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBlob &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
