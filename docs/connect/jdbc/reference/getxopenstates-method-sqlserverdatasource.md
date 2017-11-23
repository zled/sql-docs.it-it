---
title: Metodo getXopenStates (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.getXopenStates
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f90ff3fc2c843540fb9a95038203c9ce60d0b432
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Metodo getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un **booleano** valore che indica se la conversione di stati SQL in stati conformi a XOpen è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la conversione di stati SQL in stati conformi a XOpen è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà xopenStates è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertirà stati SQL in stati conformi a XOpen. Il valore predefinito è **false**, causando il driver JDBC generare codici di stato SQL 99. Se xopenStates non è impostata, il metodo getXopenStates restituisce il valore predefinito di **false**.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
