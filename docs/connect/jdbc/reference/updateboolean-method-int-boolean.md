---
title: Metodo updateBoolean (int, boolean) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBoolean (int, boolean)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7937f4bb-8537-4012-af81-837f9ac123a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f3c6aecfc512f1b3c6afa15c5881dea31e1ee60
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798439"
---
# <a name="updateboolean-method-int-boolean"></a>Metodo updateBoolean (int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore **boolean** in base all'indice della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBoolean(int index,  
                          boolean x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *x*  
  
 Valore **booleano**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateBoolean viene specificato dal metodo updateBoolean nell'interfaccia ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBoolean &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
