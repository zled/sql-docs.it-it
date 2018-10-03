---
title: Metodo setServerPreparedStatementDiscardThreshold (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d008e26d4eb7e6c2ac4b362f03ce3b2716a4cc46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655029"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Metodo setServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Specifica il comportamento per un'istanza di connessione specifica. Questa impostazione Controlla quanti preparato in sospeso variabile discard istruzione azioni (sp_unprepare) possono rimanere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Quando l'impostazione è < = 1 ONU-preparare le azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se il valore è impostato su 1 > queste chiamate vengono eseguite in batch insieme per evitare il sovraccarico della chiamata al metodo sp_unprepare troppo spesso.


## <a name="syntax"></a>Sintassi  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Parametri  
 *thresholdValue*  
 
 Il nuovo valore della **serverPreparedStatementDiscardThreshold** proprietà di connessione.  
 
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e progressiva.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
