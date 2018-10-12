---
title: Metodo setPoolable (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 809e16fce7cac83b6ba09fcef676c8da920b0dc3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759679"
---
# <a name="setpoolable-method-sqlserverstatement"></a>Metodo setPoolable (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Richiede che un'istruzione sia o meno inserita in un pool.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Parametri  
 *in pool*  
  
 Se **true**, richiede che l'istruzione sia inserita in un pool. Se **false**, richiede che l'istruzione non sia inserita in un pool.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Il valore specificato nel parametro *poolable* è un hint per l'implementazione del pool di istruzioni che indica se l'applicazione vuole che l'istruzione sia inserita in un pool. L'utilizzo dell'hint sarà deciso tramite la gestione del pool di istruzioni.  
  
 Un valore del pool di istruzioni viene applicato sia alle cache interne dell'istruzione implementate dal driver sia a quelle esterne implementate dai server applicazioni e da altre applicazioni.  
  
 Per impostazione predefinita, questo oggetto SQLServerStatement non è in pool quando creato. Gli oggetti SQLServerPreparedStatement e SQLServerCallableStatement sono in pool quando creato.  
  
 L'eccezione [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) viene generata se questo metodo viene chiamato su un'istruzione chiusa.  
  
 L'oggetto [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) restituisce un valore che indica se l'oggetto può essere inserito in un pool.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
