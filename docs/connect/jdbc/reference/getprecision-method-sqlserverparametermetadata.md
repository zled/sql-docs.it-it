---
title: Metodo getPrecision (SQLServerParameterMetaData) | Documenti Microsoft
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
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c80beecc510fb5f2d4190839e8bc4ca1c95602c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getprecision-method-sqlserverparametermetadata"></a>Metodo getPrecision (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero di cifre decimali del parametro designato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Parametri  
 *param*  
  
 Un **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica la precisione del parametro designato.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getPrecision viene specificato dal metodo getPrecision nell'interfaccia Java.SQL. parametermetadata.  
  
 Per i tipi numerici, questo metodo ottiene il numero di cifre decimali. Per i tipi carattere, ottiene la lunghezza massima in caratteri. Per i tipi binari, ottiene la lunghezza massima in byte. Se il numero di cifre è sconosciuto, questo metodo restituisce "0".  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membri di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
