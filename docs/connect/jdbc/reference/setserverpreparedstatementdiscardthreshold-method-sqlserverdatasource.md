---
title: Metodo setServerPreparedStatementDiscardThreshold (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c47579114bab412a68698ef4c589ba32673328a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824009"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>Metodo setServerPreparedStatementDiscardThreshold (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore della proprietà di connessione serverPreparedStatementDiscardThreshold. Questa impostazione Controlla quanti preparato in sospeso variabile discard istruzione azioni (sp_unprepare) possono rimanere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Quando l'impostazione è < = 1 unprepare azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se il valore è impostato su 1 > queste chiamate vengono eseguite in batch insieme per evitare il sovraccarico della chiamata al metodo sp_unprepare troppo spesso
 
## <a name="syntax"></a>Sintassi  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Parametri  
 *serverPreparedStatementDiscardThreshold*  
  
 Il nuovo valore della **serverPreparedStatementDiscardThreshold** proprietà di connessione.  

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e progressiva.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
