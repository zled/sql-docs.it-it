---
title: Metodo updateDouble (int, double) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateDouble (int, double)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90c47643-e27e-425d-85a0-63866f858367
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 243d42ed167c1722cea796215af192213614b22f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746779"
---
# <a name="updatedouble-method-int-double"></a>Metodo updateDouble (int, double)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore **double** in base all'indice della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateDouble(int index,  
                         double x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *x*  
  
 Oggetto **doppie** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateDouble viene specificato dal metodo updateDouble nell'interfaccia ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateDouble &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
