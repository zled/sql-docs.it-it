---
title: Metodo setEscapeProcessing (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.setEscapeProcessing
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5e7c53393acca2a1ad95d590ce28fbd7b943b534
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setescapeprocessing-method-sqlserverstatement"></a>Metodo setEscapeProcessing (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta la modalità di elaborazione di escape.  
  
> [!NOTE]  
>  Per l'elaborazione di escape [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] è sempre abilitata. L'impostazione di questo metodo su false non ha effetti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### <a name="parameters"></a>Parametri  
 *abilitare*  
  
 **true** per abilitare l'elaborazione di escape. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setEscapeProcessing viene specificato dal metodo setEscapeProcessing nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
