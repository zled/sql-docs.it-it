---
title: Metodo (SQLServerConnection) getEnablePrepareOnFirstPreparedStatementCall | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 624072532d643d9a335533b861ae0184171ba259
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Restituisce il valore di **enablePrepareOnFirstPreparedStatementCall** proprietà di connessione. Se false, la prima esecuzione chiamerà sp_executesql e preparare un'istruzione, dopo l'esecuzione del secondo caso chiameremo sp_prepexec e consentono di impostare un handle di istruzione preparata. Seguenti esecuzioni chiamerà sp_execute. Questo elimina la necessità di sp_unprepare in istruzione preparata chiudere se l'istruzione viene eseguita solo una volta. Il valore predefinito per questa opzione può essere modificato dalla chiamata setDefaultEnablePrepareOnFirstPreparedStatementCall().

## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Valore restituito
 Oggetto **booleano** che contiene il valore di **enablePrepareOnFirstPreparedStatementCall** proprietà di connessione.

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
