---
title: Metodo getHoldability (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9cf27049e45c8e52c8a63a419327f377dd1f558f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841399"
---
# <a name="getholdability-method-sqlserverresultset"></a>Metodo getHoldability (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la trattenibilità di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** contenente uno dei livelli di trattenibilità seguenti:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getHoldability viene specificato dal metodo getHoldability nell'interfaccia ResultSet.  
  
 Per impostare la trattenibilità del set di risultati, le applicazioni possono usare il metodo [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) della classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md). Dopo che è stato chiamato il metodo [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md), sono stati creati l'oggetto istruzione e il rispettivo oggetto del set di risultati ed è stata eseguita l'istruzione, può essere necessario modificare di nuovo la trattenibilità.  
  
 Per i cursori sul lato server, se connessi a SQL Server 2005 o versioni successive, l'impostazione influisce solo sulla trattenibilità dei nuovi set di risultati ancora da creare in tale connessione. In SQL Server 2000, tuttavia, l'impostazione influisce sulla trattenibilità sia dei set di risultati esistenti che in quelli nuovi ancora da creare in tale connessione.  
  
 Quando viene reimpostata la trattenibilità e viene chiamato il metodo getHoldability su oggetti di set di risultati creati in precedenza, il valore restituito da questo metodo può essere diverso dal valore di trattenibilità restituito dai metodi seguenti: Statement.getResultSetHoldability , Connection.getHoldability o DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
