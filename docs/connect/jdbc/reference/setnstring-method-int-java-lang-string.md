---
title: Metodo (int, lang) setNString | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7da6d44-f5b1-44f8-95f5-40179968b1b0
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 31b42f0d3efb69cd1bf27c05b5aeaf10b518ec4a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setnstring-method-int-javalangstring"></a>Metodo setNString (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sull'oggetto specificato **stringa** oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNString(int parameterIndex,  
                                                  java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Un **int** che indica l'indice del parametro.  
  
 *Valore*  
  
 Oggetto **stringa** oggetto che contiene il valore del parametro.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo deve essere utilizzato per **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** tipi di dati.  
  
 Questo metodo setNString viene specificato dal metodo setNString nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
