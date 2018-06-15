---
title: Metodo (SQLServerDataSource) getEnablePrepareOnFirstPreparedStatementCall | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a131964479c0e2f64afa1f316344d446d1df2214
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32834542"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall metodo (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il valore di **enablePrepareOnFirstPreparedStatementCall** proprietà di connessione. Se questa configurazione restituisce false la prima esecuzione di un'istruzione preparata verrà chiamato sp_executesql e non prepara un'istruzione, una volta che si verifica la seconda esecuzione verrà chiamata sp_prepexec e del programma di installazione effettivamente un handle di istruzione preparata. Seguenti esecuzioni chiamerà sp_execute. Questo elimina la necessità di sp_unprepare in istruzione preparata chiudere se l'istruzione viene eseguita solo una volta. 
  
## <a name="syntax"></a>Sintassi  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il **booleano** valore il **enablePrepareOnFirstPreparedStatementCall** proprietà di connessione.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
