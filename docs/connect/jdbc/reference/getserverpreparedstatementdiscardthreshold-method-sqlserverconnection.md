---
title: Metodo (SQLServerConnection) getServerPreparedStatementDiscardThreshold | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.getServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39ff0c7fcda4a814d3e9e1347c2b04fb89f699e7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32837372"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>getServerPreparedStatementDiscardThreshold metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Restituisce il valore di **serverPreparedStatementDiscardThreshold** proprietà di connessione. Questa impostazione Controlla preparato in sospeso quanti Ignora istruzione azioni (sp_unprepare) possono essere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Se l'impostazione è < = 1, unprepare azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se è impostato su 1 >, queste chiamate sono raggruppate per evitare l'overhead della chiamata sp_unprepare troppo spesso. Il valore predefinito per questa opzione può essere modificato dalla chiamata getDefaultServerPreparedStatementDiscardThreshold().

## <a name="syntax"></a>Sintassi  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Valore restituito
 Un **int** che contiene il valore di **serverPreparedStatementDiscardThreshold** proprietà di connessione.

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
