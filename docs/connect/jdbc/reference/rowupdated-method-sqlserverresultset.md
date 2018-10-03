---
title: Metodo rowUpdated (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowUpdated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40afdf8854e40050e718b9c456eaf0a41f7430b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614927"
---
# <a name="rowupdated-method-sqlserverresultset"></a>Metodo rowUpdated (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera informazioni sull'eventuale aggiornamento della riga corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la riga è stata aggiornata in modo visibile dal proprietario o un altro utente e gli aggiornamenti vengono rilevati. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo rowUpdated viene specificato dal metodo rowUpdated nell'interfaccia ResultSet.  
  
 Il valore restituito dipende dall'eventuale rilevamento degli aggiornamenti da parte del set di risultati.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non rileva righe aggiornate per qualsiasi tipo di cursore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
