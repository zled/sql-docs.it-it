---
title: Metodo getLastUpdateCount (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b7d016b1a6e91eca1752588825eae6fa2fe0bfdb
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>Metodo getLastUpdateCount (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un **booleano** valore che indica se la proprietà lastUpdateCount è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se lastUpdateCount è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà lastUpdateCount è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] restituirà solo l'ultimo conteggio aggiornamenti da un'istruzione SQL passata al server. Se la proprietà lastUpdateCount è impostata su **false**, il driver restituirà tutti i conteggi aggiornamenti, inclusi quelli restituiti dai trigger eventualmente attivati. Se la proprietà lastUpdateCount property non è impostata, il metodo getLastUpdateCount restituisce il valore predefinito di **true**.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

