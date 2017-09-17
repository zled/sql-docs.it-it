---
title: Metodo setCharacterStream (SQLServerNClob) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54ea45119a144852daff92dac5037b6f7407d259
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setcharacterstream-method-sqlservernclob"></a>Metodo setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un flusso da utilizzare per scrivere un flusso di caratteri Unicode dal **NCLOB** che questo valore **Java.SQL. NClob** oggetto, a partire dalla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 La posizione in corrispondenza del quale iniziare la scrittura di **NCLOB** valore; la prima posizione è 1.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Writer che rappresenta il flusso di caratteri Unicode a cui può essere scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCharacterStream viene specificato dal metodo setCharacterStream nell'interfaccia Java.SQL. NClob.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
