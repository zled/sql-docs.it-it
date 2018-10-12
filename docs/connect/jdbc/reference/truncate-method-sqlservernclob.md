---
title: Metodo Truncate (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b7e8210d-a724-4bae-832a-ae4c63031c9c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60378c751c2c8bacf96d7eace297eeca144f8869
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800969"
---
# <a name="truncate-method-sqlservernclob"></a>Metodo truncate (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tronca l'oggetto **NCLOB** in base alla lunghezza specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Parametri  
 *len*  
  
 Lunghezza espressa in caratteri, in base alla quale deve essere troncato l'oggetto **NCLOB**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo troncamento è specificato dal metodo nell'interfaccia java.sql.NClob truncato.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
