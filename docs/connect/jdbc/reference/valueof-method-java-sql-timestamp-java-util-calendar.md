---
title: Metodo valueOf (Java.SQL. timestamp, java.util.Calendar) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b77f9ce80c54980a8a55d23b90667e2c07672caa
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Metodo valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un **DateTimeOffset** oggetto che rappresenta un punto nel tempo in un particolare offset GMT in base a un valore Java.SQL. timestamp e un valore di java.util.Calendar che indica l'offset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Parametri  
 *timestamp*  
  
 Valore java.sql.Timestamp.  
  
 *calendario*  
  
 Valori di offset.  I componenti di data e ora di *calendario* verrà impostato in base al *timestamp* valore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto DateTimeOffset che rappresenta il punto nel tempo dato dall'oggetto java.SQL. timestamp nel fuso orario dell'oggetto java.util.Calendar specificato.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo imposta inoltre l'oggetto java.util.Calendar al punto nel tempo dato dall'oggetto java.SQL. timestamp.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membri di DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
