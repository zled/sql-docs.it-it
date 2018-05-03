---
title: Metodo (SQLServerDataSource) getStatementPoolingCacheSize | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9f6121f87a962da167b4df46d397b0f23b68503
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getstatementpoolingcachesize-method-sqlserverdatasource"></a>getStatementPoolingCacheSize metodo (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il valore di **statementPoolingCacheSize** proprietà di connessione. Restituisce le dimensioni della cache dell'istruzione preparata per la connessione. '0' indica che la memorizzazione nella cache non abilitata.
  
## <a name="syntax"></a>Sintassi  
  
```
public boolean getStatementPoolingCacheSize();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Il **int** valore il **statementPoolingCacheSize** proprietà di connessione.  

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
