---
title: Metodo (int, lang) setNString | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
ms.assetid: b7da6d44-f5b1-44f8-95f5-40179968b1b0
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d427a819657cd04a7eabb07653f55eb99edc8652
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
